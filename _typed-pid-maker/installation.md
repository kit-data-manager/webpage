---
title: Installing the Typed PID Maker
breadcrumbs: /typed-pid-maker/installation
layout: default
description: Build and start the service.
repository_url: https://github.com/kit-data-manager/pit-service
repository_name: kit-data-manager/pit-service
navigation_id: typed_pid_maker_index
---

# {{ page.title }}

## Docker container

Not yet available, but planned.

## Build from Source

In order to build the Typed PID Maker, you'll need:

* Java SE Development Kit 11 (or OpenJDK 11) or higher

After obtaining the sources change to the folder where the sources are located perform the following steps:

```
user@localhost:/home/user/typed-pid-maker$ ./gradlew build
> Configure project :
Using release profile for building notification-service
<-------------> 0% EXECUTING [0s]
[...]
user@localhost:/home/user/typed-pid-maker$
```

The Gradle wrapper will now take care of downloading the configured version of Gradle and finally build the Typed PID Maker microservice.
As a result, a jar file containing the entire service is created at `build/libs/TypedPIDMaker-$(version).jar`.


## Start from JAR file

Before you are able to start the microservice, you have to modify the file 'application.properties' according to your local setup. 
Therefor, copy the file `conf/application.properties` to your project folder and customize it.
For the Collection API you just have to adapt the properties of `spring.datasource` and you may change the `server.port` property.
All other properties can be ignored for the time being.

As soon as you finished modifying 'application.properties', you may start the service by executing the following command inside the project folder, 
e.g. where the service has been built before:

```
user@localhost:/home/user/typed-pid-maker$ ./build/libs/TypedPIDMaker-$(version).jar

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::        (v2.0.5.RELEASE)
[...]
1970-01-01 00:00:00.000  INFO 56918 --- [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat started on port(s): 8070 (http) with context path ''

```

As soon as the microservice is started, you can browse to 

http://localhost:8060/swagger-ui.html

in order to see available RESTful endpoints and their documentation.
The port may vary depending on the `configuration.properties` file
You may have to adapt the port according to your local settings.
Furthermore, you can use this Web interface to test single API calls in order to get familiar with the service. 
