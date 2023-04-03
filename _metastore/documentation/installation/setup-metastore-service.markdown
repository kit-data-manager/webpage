---
title:  Setup Metastore Service (Debian)
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
user@server:~# git clone https://github.com/kit-data-manager/metastore2.git
user@server:~# cd indexing-service
```
Determine latest version:
```
user@server:~/indexing-service# git tag -l |tail -1
v1.2.1
```
Checkout latest version:
```
user@server:~/indexing-service# git checkout v1.2.1
Note: switching to 'v1.2.1'.
[...]
HEAD is now at 2c18bff  [Gradle Release Plugin] - pre tag commit:  'v1.2.1'.
```
Build indexing-service:
```
root@server:~# bash build.sh /PATH/TO/INSTALLATION/DIR
---------------------------------------------------------------------------
Build microservice of metastore2 at '/PATH/TO/INSTALLATION/DIR'
---------------------------------------------------------------------------
Build service...

> Configure project :
Running gradle version: 7.6
Building metastore2 version: 1.2.1
JDK version: 11
Using minimal profile for building metastore2
Create bootable jar...
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
# Setup paths for schema and metadata
###############################################################################
metastore.schema.schemaFolder:file:///PATH/TO/INSTALLATION/DIR/schema
metastore.metadata.metadataFolder:file:///PATH/TO/INSTALLATION/DIR/metadata

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

################################################################################
# Search - Elasticsearch
# It's recommended to install elasticsearch behind a firewall with no direct 
# access from clients.
###############################################################################
repo.search.enabled = true
repo.search.url = http://localhost:9200

###############################################################################
# Database (PostGres) 
###############################################################################
spring.datasource.url: jdbc:postgresql://localhost:5432/metastore
spring.datasource.username: metastore_admin
spring.datasource.password: METASTORE_ADMIN_PASSWORD
```
## Setup Database 4 MetaStore
```bash=bash
root@server:~# su -c psql postgres
psql (13.5 (Debian 13.5-0+deb11u1))
Type "help" for help.

postgres=# CREATE DATABASE metastore;
CREATE DATABASE
postgres=# CREATE USER metastore_admin WITH ENCRYPTED PASSWORD 'METASTORE_ADMIN_PASSWORD';
CREATE ROLE
postgres=# GRANT ALL PRIVILEGES ON DATABASE metastore TO metastore_admin;
GRANT
postgres=# \q
root@server:~# 
```
Congratulations: You are done! 

<style>
td, th {
   border: none!important;
}
</style>
| [<< PREVIOUS](setup-indexing-service.html) |[NEXT >>](setup-systemd.html)|
|:----|----:|
| | |
