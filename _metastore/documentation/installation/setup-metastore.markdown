---
title:  Configuration MetaStore
breadcrumbs: /metastore/documentation/installation/Configuration MetaStore
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
# Landing Page (since v1.4.0)
NOTE
: If you use an external UI for MetaStore (e.g. frontend-collection) which also
provides a landing page you may adopt the settings like explained above.

```
###############################################################################
# Landing Page (Schema & Metadata Documents)
#   Redirect to internal or external landing page.
#   The string may contain two placeholders for substitution:
#     - $(id) - Identifier of the digital object (mandatory)
#     - $(version) - Version of the digital object (optional) 
#
#  e.g.: https://www.example.org/landingpage?id=$(id)&version=$(version)
#
#  For frontend-collection use metastore-landing-page.html?pid=$(id)
#  e.g. https://HOSTNAME/metastore-landing-page.html?pid=$(id)&version=$(version)
#
#  Defaults: (internal landing page)
#     - /schema-landing-page?schemaId=$(id)&version=$(version) (schema documents)
#     - /metadata-landing-page?id=$(id)&version=$(version)     (metadata documents)
###############################################################################
metastore.schema.landingpage:/schema-landing-page?schemaId=$(id)&version=$(version)
metastore.metadata.landingpage:/metadata-landing-page?id=$(id)&version=$(version)
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
# Authentication
NOTE
: jwtSecret has to be configured if you want to use the search functionality
together with authentication. In that case the jwtSecret of MetaStore and 
indexing-service should contain the same value.

```
###############################################################################
# KIT DM settings for authentication
###############################################################################
# The authentication is disabled by default. If you want to enable it, please
# uncomment the following lines and adapt them to your needs.
#repo.auth.enabled:true

# The jwtSecret is used to sign the JWT token. The secret must be the same as in
# the indexing-service.
# !!! The secret must be at least 43 characters long. !!!
repo.auth.jwtSecret:add+your+long+secret+key+here.+Please+replace+this+with+your+own+secret+key

# The following line is used to restrict creating documents to a given role.
# If not set, everybody who is authenticated is authorized to create documents.
# To restrict creating to a given role, please uncomment the following line and
# adapt it to your needs.
#metastore.postEnabledForRole:USER
```
Since 2.0.2 there is a new property to restrict the creation of documents to a given role.
If not set, everybody who is authenticated is authorized to create documents.
```
# Example for restricting creating documents to a given role (USER)
metastore.postEnabledForRole:USER
``` 

```
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
repo.messaging.username:guest
repo.messaging.password:guest
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
###############################################################################
# Search - Elasticsearch
# It's recommended to install elasticsearch behind a firewall with no direct 
# access from clients.
###############################################################################
repo.search.enabled: false
# Property defining the elasticsearch URL.
repo.search.url: http://localhost:9200
# Property defining (duplicated) http headers to be removed from the response before sending it to the client.
# This is necessary because elasticsearch returns the header "Transfer-Encoding: chunked"
# which is not allowed by some tools.
# Default: Transfer-Encoding
#repo.search.dedupHeaders: Transfer-Encoding
# Property defining patterns for the endpoints to be used by the search proxy.
# Multiple patterns can be defined by separating them with a comma.
# The default pattern is: /[^/]+)?/api/v\d+(/[^/]+)?/_?search$
# Examples: /context/api/v1/search, /context/api/v1/metadata/_search
#repo.search.endpointPattern: (/[^/]+)?/api/v\d+(/[^/]+)?/_?search$
```
Since 2.0.2 there is a new property to deduplicate headers which were created while executing search via proxy.
If not set, the header "Transfer-Encoding: chunked" is returned twice which is not allowed by some tools.
(e.g. traefik middleware)
The default value is "Transfer-Encoding".

The deduplication is only done for the search endpoints.
Endpoints which are not matching the pattern defined in "repo.search.endpointPattern" are not affected.
You can define multiple patterns by separating them with a comma.


The default pattern is: /[^/]+)?/api/v\d+(/[^/]+)?/_?search$

Examples: /context/api/v1/search, /context/api/v1/metadata/_search
```
# Example for deduplication of headers
repo.search.dedupHeaders: Transfer-Encoding
repo.search.endpointPattern: (/[^/]+)?/api/v\d+(/[^/]+)?/_?search$
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

Since 2.0.2 the available endpoints are limited to info and health by default.
For security reasons you may disable all endpoints but you ***shouldn't*** add additional
ones.
```
###############################################################################
# Management endpoint settings
###############################################################################
management.endpoints.enabled-by-default: false
management.endpoint.info.enabled: true
management.endpoint.health.enabled: true
management.endpoint.health.show-details: WHEN-AUTHORIZED
management.endpoint.health.sensitive: false
management.endpoints.web.exposure.include: info, health
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
# Management Prometheus Endpoint
Since 2.1.0 the prometheus endpoint is available but disabled by default.
To enable it, please uncomment the following line and adapt it to your needs.
```
###############################################################################
# Monitoring
###############################################################################
# If you want to use the monitoring service, please uncomment the following
# lines and adapt them to your needs.
# Enable the monitoring service (Default: false)
#metastore.monitoring.enabled: true
###############################################################################
# ATTENTION: Enable also management endpoint for monitoring if you want to use it
###############################################################################
#management.endpoint.prometheus.enabled: true
#management.endpoints.web.exposure.include: prometheus
###############################################################################
# Configuration for Monitoring
###############################################################################
# Configure how often the monitoring service should check the status of the
# repository. The default is once an hour. (0 3 * * * *)
#   |-------------- second
#   | |------------ minute
#   | | |---------- hour
#   | | | |-------- day of month
#   | | | | |------ month
#   | | | | | |---- day of week
#   | | | | | |
#   * * * * * *
metastore.monitoring.cron4schedule: 0 3 * * * *
# Configure how often the monitoring service should clean up the database
# removing accessing hashes older than 'noOfDaysToKeep'.
# The default is once a day at midnight. (0 0 0 * * *)
metastore.monitoring.cron4cleanUp: 0 0 0 * * *
# Configure how long the monitoring service should keep the data in the
# database. The default is 28 days. (28)
metastore.monitoring.noOfDaysToKeep: 28
# Configure the maximum number of schemas for which the monitoring service
# should collect the number of documents. The default is 10.
metastore.monitoring.noOfSchemas: 10
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
#keycloakjwt.jwk-url=<keycloak-jwk-endpoint, e.g.: http://localhost:8080/auth/realms/<keycloak-realm>/protocol/openid-connect/certs>
#keycloakjwt.resource=<client-identifier-in-realm>
#keycloakjwt.jwt-claim=preferred_username
##keycloakjwt.connect-timeoutms=500 //optional
##keycloakjwt.read-timeoutms=500 // optional
#
#keycloak.realm = <keycloak-realm>
#keycloak.auth-server-url = <keycloak-auth-url, e.g.: http://localhost:8080/auth>
#keycloak.resource =<client-identifier-in-realm> 
```
After editing all relevant settings the service has to be restarted!


