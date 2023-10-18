---
title:  Setup MetaStore
breadcrumbs: /metastore/documentation/installation/Setup MetaStore
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_instal
---

# {{ page.title }} 
For using MetaStore in a production environment the service has to be configured.
For doing so please **copy** the file 'application.properties' to the 'config' subdirectory.
The 'application.properties' in the config directory overwrites all settings of the file in
the parent directory. Therefor you may delete all settings from the 'config/application.properties'
you don't want to change.

NOTE
: If you only want to remove properties (and not change them), they must be commented out 
('#' at the beginning of the line) in 'application.properties'.

The default configuration may look like this:
```
###############################################################################
# Server settings
###############################################################################
```
# Port

```
###############################################################################
# Port
###############################################################################
server.port: 8040
```
# Forwarded Headers (Proxy)
ATTENTION
: If you would like to use the service behind a proxy, you will need to 
uncomment this line.

```
###############################################################################
# Proxy (enable this line if you want to use the service behind a proxy.)
###############################################################################
#server.forward-headers-strategy=framework
```

# Paths
ATTENTION
: Directories must be writable by the service!

```
###############################################################################
# Setup paths for schema and metadata
###############################################################################
metastore.schema.schemaFolder:file:///tmp/metastore2/schema
metastore.metadata.metadataFolder:file:///tmp/metastore2/metadata
```
NOTE
: Leave the file management section unchanged if you do not expect more than 10,000 files per month.
Otherwise, configure the directory structure more fine-grained or switch to ID-based management.


```
###############################################################################
# Setup folder management for metadata documents
# Note: Creating more than 50.000 directories inside one directory might cause
#       performance issues. 
# Possible values: 
# - simple (No hierarchie at all)
# - idBased (Split ID in small parts and create directory structure out of it)
# - dateBased (Create directory structure by date) (default) 
###############################################################################
metastore.metadata.storagepattern:dateBased

# Configuration for 'idBased' e.g. 4ca2cc62-df0b-49b1-b622-ce855554adfc -> 4ca2/cc62/df0b/49b1/b622/ce85/5554/4ca2cc62df0b49b1b622ce855554adfc
# default: charPerDirectory: 4, maxDepth: 7
repo.plugin.storage.id.charPerDirectory:4
repo.plugin.storage.id.maxDepth:7

# Configuration for 'dateBased' e.g.: @{year}/@{year}_@{month}_@{day}_@{hour}_@{minute}
# default: @{year}/@{month}
repo.plugin.storage.date.pathPattern:@{year}/@{year}_@{month}_@{day}_@{hour}_@{minute}

###############################################################################
# Setup schema registries. (Optional, no longer necessary)
###############################################################################
#metastore.metadata.schemaRegistries:http://localhost:8040/api/v1/
```
# OAI PMH
NOTE
: Make sure that your service is accessible. Replace 'localhost' by the 
full qualified hostname of your server/proxy.

```
###############################################################################
# OAI PMH Plugin
###############################################################################
repo.plugin.repositoryBaseUrl:http://localhost:8040/api/v1/metadata
repo.plugin.oaipmh.adminEmail:admin@example.org
repo.plugin.oaipmh.maxElementsPerList:10
```
# DOIP
```
###############################################################################
# DOIP Plugin
###############################################################################
repo.plugin.doip.enabled: false
repo.plugin.doip.port: 41420
repo.plugin.doip.serviceId:35.TEST/DOIPServer
repo.plugin.doip.serviceName:DOIP4MetaStore
repo.plugin.doip.serviceDescription:Generic repository especially for metadata.
# 'localhost' has to be replaced by hostname
repo.plugin.doip.address:localhost
repo.plugin.doip.authenticationEnabled:true
repo.plugin.doip.defaultToken:REPLACE_BY_YOUR_TOKEN
```
# Logging
NOTE
: These values should only be changed for debugging reasons.

```
###############################################################################
# Logging settings
###############################################################################
logging.level.root: ERROR
logging.level.edu.kit: WARN
```
# Token Management
NOTE
: jwtSecret has to be configured if you want to use the search functionality
together with authentication. In that case the jwtSecret of MetaStore and 
indexing-service should contain the same value.

```
###############################################################################
# KIT DM settings
###############################################################################
repo.auth.jwtSecret: NOT+USED+RIGHT+NOW+YOU+MAY+CHANGE+IF+NECCESSARY

###############################################################################
# KIT DM JaVers settings
###############################################################################
## Default should be OK. Only set to higher value if problems occur.
# metastore.javers.scope: 20
```
# [RabbitMQ](messaging/messaging-introduction.html)
NOTE
: In case you want to use the search functionality you have to enable the messaging.
Messaging is used to inform indexing-service about new/updated metadata documents.
: For further information please refer to [RabbitMQ introduction](messaging/messaging-introduction.html)

```
###############################################################################
# Messaging - RabbitMQ
###############################################################################
repo.messaging.enabled: false
repo.messaging.hostname:localhost
repo.messaging.port:5672
repo.messaging.sender.exchange: metastore_events
# Settings for receivers.
###############################################################################
#repo.schedule.rate:1000
#repo.messaging.receiver.exchange: metastore_events
#repo.messaging.receiver.queue: metastoreEventQueue
#repo.messaging.receiver.routingKeys: metadata.#
```
# Elasticsearch
NOTE
: In case you want to use the search functionality you have to enable the search
and provide a valid URL to elasticsearch. Otherwise the service will not start.

```
################################################################################
# Search - Elasticsearch
# It's recommended to install elasticsearch behind a firewall with no direct 
# access from clients.
###############################################################################
repo.search.enabled = false
repo.search.url = http://localhost:9200
```
# Database Settings
ATTENTION
: If you want to use another database please make sure, that the following lines
are disabled in ***ALL*** application.properties files!

```
##############################################################################
# Database
###############################################################################
spring.datasource.driver-class-name: org.h2.Driver
spring.datasource.url:  jdbc:h2:file:./database/metastore;MODE=LEGACY;NON_KEYWORDS=VALUE
spring.datasource.username: any
spring.datasource.password: any
spring.jpa.hibernate.ddl-auto: update
   
###############################################################################
# Spring Cloud
###############################################################################
# Disable cloud configuration
spring.cloud.config.enabled=false
eureka.client.enabled=false

###############################################################################
# Spring Data Rest
###############################################################################
spring.data.rest.detection-strategy:annotated
```
# Management Health Endpoint
Use this [site](https://docs.spring.io/spring-boot/docs/2.1.7.RELEASE/reference/html/production-ready-endpoints.html#production-ready-health) to get a deeper insight.

```
###############################################################################
# Management endpoint settings
###############################################################################
management.endpoint.health.enabled: true
management.endpoint.health.show-details: WHEN-AUTHORIZED
management.endpoint.health.sensitive: false
management.endpoints.web.exposure.include: *
# Disable unused service
# Remove or enable the corresponding lines if you want to check the health of 
# dependent services as well.
management.health.elasticsearch.enabled: false
management.health.rabbit.enabled: false

spring.main.allow-bean-definition-overriding:true

###############################################################################
# Add detailed message to REST response (NOT RECOMMENDED for PRODUCTION MODE)
# If this is disabled, the error messages of the GUI are unfortunately 
# no longer meaningful.
###############################################################################
server.error.include-message=always
```
# CSRF
For accessing the service from a frontend the URL of the frontend has to be
configured as allowed origin.
```
###############################################################################
# Disable Cross-Site-Request-Forgery (NOT RECOMMENDED for PRODUCTION MODE)
# Please adapt origin patterns to your needs
###############################################################################
metastore.security.enable-csrf=false
metastore.security.allowedOriginPattern=http*://localhost:*
```
# Keycloak
ATTENTION
: If you want to add keycloak to your configuration please make sure, that the 
'spring.autoconfigure.exclude' is disabled in ***ALL*** application.properties files.

```
###############################################################################
# If you want to use Keycloak please disable first line and enable 
# the following lines and adapt to your needs. 
###############################################################################
### Following line disables keycloak filters.
spring.autoconfigure.exclude=org.keycloak.adapters.springboot.KeycloakAutoConfig
uration,org.springframework.boot.autoconfigure.security.servlet.SecurityAutoConf
iguration
#keycloakjwt.jwk-url=http://localhost:8080/auth/realms/myrealm/protocol/openid-c
onnect/certs
#keycloakjwt.resource=keycloak-angular
#keycloakjwt.jwt-claim=preferred_username
##keycloakjwt.connect-timeoutms=500 //optional
##keycloakjwt.read-timeoutms=500 // optional
#
#keycloak.realm = myrealm
#keycloak.auth-server-url = http://localhost:8080/auth
#keycloak.resource = keycloak-angular
```
After editing all relevant settings the service has to be restarted!


