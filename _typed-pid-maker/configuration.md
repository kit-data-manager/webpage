---
title: Configuring the Typed PID Maker
breadcrumbs: /typed-pid-maker/installation
layout: default
description: Port, messaging, PID Service authentication.
repository_url: https://github.com/kit-data-manager/pit-service
repository_name: kit-data-manager/pit-service
navigation_id: typed_pid_maker_index
---

# {{ page.title }}

There are a couple of configuration options which are described here.
All configuration is done in the file 'application.properties'.
There is a [well-documented example-configuration in the Typed PID Maker code repository](https://github.com/kit-data-manager/pit-service/blob/master/config/application.properties).
This document explains the basic configuration in a more structured way for an easy introduction.

Spring Boot offers different ways of providing the configuration to a service.
For the Typed PID Maker, three options are relevant, whereas "current directory" describes the directory, where TypedPidMaker-$(version).jar is located:

- In a /config subfolder of the current directory.
- In the current directory
- Provided as command line argument -Dspring.config.location=[absolute path to application.properties]

Generally, all [listed properties] offered by the Spring Framework are supported, but only a few of them are used by default.
With the source code comes a default application.properties, already containing all relevant properties with default values.
Most of them can be changed according to local needs, properties which should not be changed are marked accordingly.
For information on Spring properties, please refer to the official documentation.

Furthermore, there are several properties to configure the Typed PID Maker instance itself.
We document these properties in the following sections, as well as in the inline documentation in the sample application.properties.

[listed properties]: https://docs.spring.io/spring-boot/docs/current/reference/html/application-properties.html

## Service Configuration

As most of these properties are understandable by their name, we take only an excerpt here.
Refer to the inline documentation of the example configuration for details.

- Port. `server.port: 8060` sets the port for the REST interface.
- Logging: You can set the level of logging for each module independently. Example:

    ```properties
    logging.level.root: ERROR
    #logging.level.edu.kit.datamanager.doip: TRACE
    logging.level.edu.kit.datamanager.pit.pidsystem.impl: WARN
    logging.level.edu.kit: WARN
    logging.level.org.springframework: ERROR
    logging.level.org.springframework.amqp: WARN
    ```

## Message Broker

Enable (default)/disable messaging.
The messaging functionality requires a RabbitMQ server receiving and distributing the messages sent by the Typed PID Maker.
`repo.messaging.hostname` and `repo.messaging.port` describe the access information for the RabbitMQ server.
The `repo.messaging.sender` property contains properties which are specific for sending messages,
in contrast to `repo.messaging.receiver`, which is specific to receiving messages, and not relevant to the Typed PID Maker.
`repo.messaging.sender.exchange` defines an [exchange] name to use. Example:

[exchange]: https://www.baeldung.com/java-rabbitmq-exchanges-queues-bindings#exchanges

```properties
repo.messaging.enabled: false
repo.messaging.hostname: localhost
repo.messaging.port: 5672
repo.messaging.sender.exchange: record_events
```

## PID Service

The current version ships with a Handle implementation which uses the Handle Protocol (in contrast to the REST interface).
It uses the official Handle Java Client Library and is therefore considered reliable.

There are further implementations which will not create globally resolvable PIDs.
We call those "sandboxed PIDs", and their purpose is mostly for testing or special use-cases.
There is a "Local PID System" implementation, which stores PIDs in a local database.
PIDs will then only be resolvable using this instance of the Typed PID Maker.
Alternatively, you can choose an In-Memory-Implementation to create sandboxed PIDs which do only last until the service stops.
PIDs will not be a available after starting the service again, and you'll have to begin from scratch.

You can choose an implementation by specifying it like this:

```properties
pit.pidsystem.implementation = LOCAL # other values: HANDLE_PROTOCOL, IN_MEMORY
```

Depending on this setting, other settings might be available:

The IN_MEMORY implementation does currently not have any settings.

The LOCAL implementation depends on the general database configuration of the whole instance.
These settings are always available and should be set properly:

```properties
####################################
# Storing known PIDs in a database #
### (Also required for messaging) ##
####################################
# This database will always run, as it is also required for the messaging feature,
# but for the messaging it is not required to be persistent.
# But the service will also use this database to store known PIDs.
# This can be used as a backup or documentation of all PIDs.
# The following properties can (and should) be set.
# The driver detemins the database system to start. Other drivers are untested, but may work.
spring.datasource.driver-class-name: org.h2.Driver
# Next, please choose a location for the database file on your file system.
# WARNING: If no url is being defined, an in-memory database is being used,
#          loosing all data on restart.
# WARNING: Change the DB to be stored somewhere outside of /tmp!
spring.datasource.url:  jdbc:h2:file:/tmp/database;MODE=LEGACY;NON_KEYWORDS=VALUE
# Credentials for the database:
spring.datasource.username: <your user name here>
spring.datasource.password: <your password here>
# Do not change ddl-auto if you do not know what you are doing:
# https://docs.spring.io/spring-boot/docs/1.1.0.M1/reference/html/howto-database-initialization.html
spring.jpa.hibernate.ddl-auto: update
```

The HANDLE_PROTOCOL implementation requires keys and certificates to access the PID service:

```properties
# prefix string
pit.pidsystem.handle-protocol.credentials.handleIdentifierPrefix = 00.A00000
# PID of user to authenticate
pit.pidsystem.handle-protocol.credentials.userHandle = 00.A00000/USER01
# Path to key/certificate file.
pit.pidsystem.handle-protocol.credentials.privateKeyPath = config/00.A00000_USER01_300_privkey.bin 
```

If your key file is password-protected, you can set the password via the environment variable `handleProtocolPrivateKeyPassphrase`.

When resolving PIDs for validation, the following resolver URL is currently used: `pit.pidsystem.handle.baseURI = http://hdl.handle.net/`
This property is likely subject to change.

## Type Registry

The Typed PID Maker uses a Data Type Registry (DTR) for validation.
The registry must (currently) be compatible with the ePIC DTR.
By default, the ePIC Test-DTR is configured:

```properties
pit.typeregistry.baseURI = http://dtr-test.pidconsortium.eu/
```

By changing this value to `http://dtr.pidconsortium.eu/`, you can change to the production instance.