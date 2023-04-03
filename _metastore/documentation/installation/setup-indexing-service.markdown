---
title:  Install Indexing-Service
breadcrumbs: /metastore/documentation/installation
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_instal
---

# {{ page.title }} 
--- 
NOTE
:  Right now only elasticsearch 7.x is supported by MetaStore and Indexing-Service.

--- 
## Requirements
- JAVA 11 or higher (JDK)
- Git
- Python (3.6 or higher)
- PostgreSql

## Build Indexing-Service
The first step is to download the repository from git:
```
user@server:~# git clone https://github.com/kit-data-manager/frontend-collection.git
user@server:~# cd indexing-service
```
Determine latest version:
```
user@server:~/indexing-service# git tag -l |tail -1
v0.1.3
```
Checkout latest version:
```
user@server:~/indexing-service# git checkout v0.1.3
Note: switching to 'v0.1.3'.
[...]
HEAD is now at db1ef59  [Gradle Release Plugin] - pre tag commit:  'v0.1.3'.
```
Build indexing-service:
```
root@server:~# bash build4docker.sh /PATH/TO/INSTALLATION/DIR
---------------------------------------------------------------------------
Build microservice of indexing-service at '/PATH/TO/INSTALLATION/DIR'
---------------------------------------------------------------------------
Build service...

> Configure project :
Running gradle version: 7.6
Building indexing-service version: 0.1.3
JDK version: 11
Using minimal profile for building indexing-service
[...]
---------------------------------------------------------------------------
Now you can start the service by calling '/PATH/TO/INSTALLATION/DIR/run.sh'
---------------------------------------------------------------------------
```
It's recommended to use the postgres database. Therefore, you need to copy the appropriate settings to /PATH/TO/INSTALLATION/DIR/application.properties:
```
user@server:~/indexing-service# cp settings/application-postgres.properties /PATH/TO/INSTALLATION/DIR/application.properties
```
Change to the installation directory to configure the service according to your needs. To do this, copy the new file with the default settings into the config directory. In the copied file, delete any lines with settings that do not need to be changed, and modify the remaining lines to suit your needs.
```
user@server:~/indexing-service# cd /PATH/TO/INSTALLATION/DIR
user@server:/PATH/.../DIR/# cp application.properties config/
```
The edited file may look like this (config/application.properties):
```
###############################################################################
# Server settings
###############################################################################
###############################################################################
# JWT secret (This should be changed if you want to use user authentication)
# It must contain the same value as defined in MetaStore.
###############################################################################
repo.auth.jwtSecret: NOT+USED+RIGHT+NOW+YOU+MAY+CHANGE+IF+NECCESSARY

###############################################################################
# Messaging - RabbitMQ
###############################################################################
repo.schedule.rate:5000
repo.messaging.enabled: true
repo.messaging.hostname:localhost
repo.messaging.port:5672

###############################################################################
# Database (PostGres) 
###############################################################################
spring.datasource.url: jdbc:postgresql://localhost:5432/indexing
spring.datasource.username: indexing_admin
spring.datasource.password: INDEXING_ADMIN_PASSWORD
################################################################################
########################        IndexingService        #########################
################################################################################
# ABSOLUTE path to the local mappings folder
################################################################################
metastore.indexer.mappingsLocation:file:///PATH/TO/INSTALLATION/DIR/mapping

################################################################################
####################### Configuration for elasticsearch ########################
################################################################################

# The base URL of the elasticsearch service, including port.
metastore.indexer.elastic.baseUrl: http://localhost:9200
```
## Setup Database 4 Indexing-Service
```bash=bash
root@server:~# su -c psql postgres
psql (13.5 (Debian 13.5-0+deb11u1))
Type "help" for help.

postgres=# CREATE DATABASE indexing;
CREATE DATABASE
postgres=# CREATE USER indexing_admin WITH ENCRYPTED PASSWORD 'INDEXING_ADMIN_PASSWORD';
CREATE ROLE
postgres=# GRANT ALL PRIVILEGES ON DATABASE indexing TO indexing_admin;
GRANT
postgres=# \q
root@server:~# 
```
Congratulations: You are done! 
    
If you want to set up a service to start automatically at startup, you might want to take a look at [Setup Server, section 'Installation as a systemd Service'](setup-systemd.html)

<style>
td, th {
   border: none!important;
}
</style>
| [<< PREVIOUS](setup-rabbitMq.html) |[NEXT >>](setup-metastore-service.html)|
|:----|----:|
| | |
