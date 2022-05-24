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

The default configuration may look like this:
```
###############################################################################
# Server settings
###############################################################################
# Port
###############################################################################
server.port: 8040

###############################################################################
# Setup paths for schema and metadata
###############################################################################
# Make sure that sufficient hard disk space is available. 
# Please change this as /tmp is not a good place for storing static files.
###############################################################################
metastore.schema.schemaFolder:file:///tmp/metastore2/schema
metastore.metadata.metadataFolder:file:///tmp/metastore2/metadata

###############################################################################
# Setup schema registries. (Optional, no longer necessary)
###############################################################################
#metastore.metadata.schemaRegistries:http://localhost:8040/api/v1/

###############################################################################
# OAI PMH Plugin
###############################################################################
# If you want to use OAI PMH please replace localhost by the fully qualified 
# hostname (e.g. https://www.example.org:8040/api/v1/metadata)
###############################################################################
repo.plugin.repositoryBaseUrl:http://localhost:8040/api/v1/metadata
repo.plugin.oaipmh.adminEmail:admin@example.org
repo.plugin.oaipmh.maxElementsPerList:10

###############################################################################
# DOIP Plugin
###############################################################################
# Don't enable this as DOIP Plugin is not production ready right now (V 1.0.0)
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


###############################################################################
# Logging settings
###############################################################################
# Only change this for debugging reasons.
# In case of debugging use 'TRACE' for the second line.
###############################################################################
logging.level.root: ERROR
logging.level.edu.kit: WARN

###############################################################################
# KIT DM settings
###############################################################################
# If authentication is used you have to create your own secret!
###############################################################################
repo.auth.jwtSecret:vkfvoswsohwrxgjaxipuiyyjgubggzdaqrcuupbugxtnalhiegkppdgjgwxsmvdb

###############################################################################
# KIT DM JaVers settings
###############################################################################
# Default should be OK. Only set to higher value if problems occur.
###############################################################################
# metastore.javers.scope: 20

###############################################################################
# Messaging - RabbitMQ
###############################################################################
# Enable this if messaging is needed 
# e.g. for indexing
###############################################################################
repo.schedule.rate:1000
repo.messaging.enabled: false
repo.messaging.hostname:localhost
repo.messaging.port:5672
repo.messaging.sender.exchange: metastore_events
repo.messaging.receiver.exchange: metastore_events
repo.messaging.receiver.queue: metastoreEventQueue
repo.messaging.receiver.routingKeys: metadata.#

###############################################################################
# Database
###############################################################################
# See Setup Database
###############################################################################
spring.datasource.driver-class-name: org.h2.Driver
spring.datasource.url:  jdbc:h2:file:/tmp/metastore2/database
spring.datasource.username: vh
spring.datasource.password: vh
spring.jpa.hibernate.ddl-auto: update
   
###############################################################################
# Spring Cloud
###############################################################################
# Don't touch the following lines
###############################################################################
# Disable cloud configuration
spring.cloud.config.enabled=false
eureka.client.enabled=false

###############################################################################
# Spring Data Rest
###############################################################################
# Don't touch the following line
###############################################################################
spring.data.rest.detection-strategy:annotated

###############################################################################
# Management endpoint settings
###############################################################################
# Don't touch the following lines
###############################################################################
management.endpoint.health.enabled: true
management.endpoint.health.show-details: ALWAYS
management.endpoint.health.sensitive: false
management.endpoints.web.exposure.include: *

spring.main.allow-bean-definition-overriding:true
spring.jpa.properties.javax.persistence.validation.mode:none

###############################################################################
# Add detailed message to REST response (NOT RECOMMENDED for PRODUCTION MODE)
# If this is disabled, the error messages of the GUI are unfortunately 
# no longer meaningful.
###############################################################################
server.error.include-message=always

###############################################################################
# Disable Cross-Site-Request-Forgery (NOT RECOMMENDED for PRODUCTION MODE)
# Please adapt origin patterns to your needs
###############################################################################
metastore.security.enable-csrf=false
metastore.security.allowedOriginPattern=http[*]://localhost:[*]

###############################################################################
# If you want to use Keycloak please disble first line and enable 
# the following lines and adapt to your needs. 
###############################################################################
### Following line disables keycloak filters.
spring.autoconfigure.exclude=org.keycloak.adapters.springboot.KeycloakAutoConfiguration,org.springframework.boot.autoconfigure.security.servlet.SecurityAutoConfiguration
#keycloakjwt.jwk-url=http://localhost:8080/auth/realms/myrealm/protocol/openid-connect/certs
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


