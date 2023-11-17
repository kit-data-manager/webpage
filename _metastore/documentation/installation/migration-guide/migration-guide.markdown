---
title:  MetaStore Migration/Update Guide 
breadcrumbs: /metastore/documentation/installation/Migration Guide
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_instal
---

# {{ page.title }} 

ATTENTION
: Before updating please stop the service. 

If you are migrating from an older version please look at all versions starting from the current version
of your installation.
If you are updating a local installation you have to copy the new jar file to the installation directory.
For older versions (< 1.3.1) you also have to overwrite run.sh with the new version. For newer versions
updating link of metastore2.jar to newest version should be sufficient.

Before starting the new version you should check the migration guide for any changes.

Add the new settings to 'application.properties' (if not recommended otherwise).
If the values should not correspond to the default value, please add the adjusted values to 
'config/application.properties'.

### Versions
- [v1.3.0](#v130)
- [v1.2.3](#v123)
- [v1.2.2](#v122)
- [v1.2.1](#v121)
- [v1.2.0](#v120)
- [v1.1.0](#v110)
- [v1.0.1](#v101)

### v1.3.0

#### System Requirements
ATTENTION
: MetaStore requires Java 17 or later. Java 8 and 11 are no longer supported. 

#### Database changes
ATTENTION
: There is a minor change in the database structure due to the upgrade to SpringBoot 3.

Please start the new version once to create the new database structure.
There will be a new sequence created called 'linked_metadata_record_seq'.
You have to set the last_value of the sequence to the maximum 'id' of 
the 'linked_metadata_record' table.

In *postgres* this could be done like follows:
```
postgres@hostname:/$ psql
psql (14.9 (Ubuntu 14.9-0ubuntu0.22.04.1))
Type "help" for help.

postgres=# \c DATABASE (see connection settings in application.properties)
You are now connected to database "DATABASE" as user "postgres".
DATABASE=# select MAX(id) from linked_metadata_record;
 max 
-----
   MAX_ID
(1 row)
DATABASE=# SELECT pg_catalog.setval('public.linked_metadata_record_seq', MAX_ID, true);
```
Replace DATABASE and MAX_ID with the values you determined. 

#### Settings
There is a new configuration option inside the application.properties:
Default context path switched from '/' to '/metastore'
In case of an update remove this line.
```
###############################################################################
# Context Path (Don't add or change once service contains documents.)
###############################################################################
server.servlet.context-path=/metastore
```
ATTENTION
: This feature MUSTN'T change afterwards. 

### v1.2.3

#### Settings
There are a new configuration options inside the application.properties:
It allows administrators to define directory structure while storing
metadata/schema documents.
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
repo.plugin.storage.date.pathPattern:@{year}/@{month}
```
### v1.2.2

#### Settings
There is a new configuration option inside the application.properties:
It allows administrators to run MetaStore service behind a proxy.
```
###############################################################################
# Proxy (enable this line if you want to use the service behind a proxy.)
###############################################################################
#server.forward-headers-strategy=framework
```

### v1.2.1
Nothing to migrate.

### v1.2.0

#### Settings
There is a new configuration option inside the application.properties:
Add actuators for info and health as default.
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
```

### v1.1.0
Nothing to migrate.

### v1.0.1

#### Database changes
ATTENTION
: Please migrate your database if you want to update MetaStore while using h2! 
See: https://h2database.com/html/migration-to-v2.html

### v1.0.0
First production ready version.



