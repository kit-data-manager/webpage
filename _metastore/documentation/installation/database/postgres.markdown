---
title:  Installation PostgreSQL (Ubuntu)
breadcrumbs: /metastore/documentation/installation/database/Installation PostgreSQL (Ubuntu)
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_instal
---

# {{ page.title }} 

## Prerequisites
- Ubuntu or something similar
- Administration rights

## Install PostgreSQL
```bash=bash
# Install postgreSQL
user@localhost:/home/user/$sudo apt install postgresql
[...]
user@localhost:/home/user/$
```
Now postgreSQL is available on localhost via port 5432.

## MetaStore
### Setup Database 4 MetaStore
```bash=bash
user@localhost:/home/user/$sudo -u postgres psql
psql (12.3 (Debian 12.3-1.pgdg100+1))
Type "help" for help.

postgres=# CREATE DATABASE metastore;
CREATE DATABASE
postgres=# CREATE USER metastore_admin WITH ENCRYPTED PASSWORD 'METASTORE_ADMIN_PASSWORD';
CREATE ROLE
postgres=# GRANT ALL PRIVILEGES ON DATABASE metastore TO metastore_admin;
GRANT
postgres=# \q
user@localhost:/home/user/$
```
Now postgreSQL is setup for MetaStore.

### Setup MetaStore2 Microservice
For using this database the settings in 'application.properties' should look like this:
```
[...]
#spring datasource settings
spring.datasource.platform: postgres
spring.datasource.url: jdbc:postgresql://localhost:5432/metastore
spring.datasource.username: metastore_admin
spring.datasource.password: METASTORE_ADMIN_PASSWORD
spring.datasource.driverClassName: org.postgresql.Driver
spring.jpa.database: POSTGRESQL
spring.jpa.database-platform: org.hibernate.dialect.PostgreSQLDialect
spring.jpa.hibernate.ddl-auto: update
[...]
```
NOTE
: Ensure that database settings for h2 are disabled!

## Indexing-Service
### Setup Database 4 Indexing-Service
NOTE
: To avoid confusion create a separate user for each service.

```bash=bash
user@localhost:/home/user/$sudo -u postgres psql
psql (12.3 (Debian 12.3-1.pgdg100+1))
Type "help" for help.

postgres=# CREATE DATABASE indexing;
CREATE DATABASE
postgres=# CREATE USER indexing_admin WITH ENCRYPTED PASSWORD 'INDEXING_ADMIN_PASSWORD';
CREATE ROLE
postgres=# GRANT ALL PRIVILEGES ON DATABASE indexing TO indexing_admin;
GRANT
postgres=# \q
user@localhost:/home/user/$
```
Now postgreSQL is setup for indexing-service.

### Setup Indexing-Service Microservice
For using this database the settings in 'application.properties' should look like this:
```
[...]
#spring datasource settings
spring.datasource.platform: postgres
spring.datasource.url: jdbc:postgresql://localhost:5432/indexing
spring.datasource.username: indexing_admin
spring.datasource.password: INDEXING_ADMIN_PASSWORD
spring.datasource.driverClassName: org.postgresql.Driver
spring.jpa.database: POSTGRESQL
spring.jpa.database-platform: org.hibernate.dialect.PostgreSQLDialect
spring.jpa.hibernate.ddl-auto: update
[...]
```
NOTE
: Ensure that database settings for h2 are disabled!

## Manage PostgreSQL
To start/stop docker service afterwards use
```bash=bash
user@localhost:/home/user/$sudo systemctl start postgresql
user@localhost:/home/user/$sudo systemctl stop postgresql
```

## Backup PostgreSQL
```bash=bash
# Backup metastore
user@localhost:/home/user/$sudo -u postgres pg_dump metastore > dump_metastore_`date +%Y_%m_%dt%H_%M`.sql"
# Backup indexing-service
user@localhost:/home/user/$sudo -u postgres pg_dump indexing > dump_indexing_`date +%Y_%m_%dt%H_%M`.sql"
```

## More Information

* [PostgreSQL (Ubuntu)](https://ubuntu.com/server/docs/databases-postgresql)
* [Backup PostgreSQL](https://www.postgresql.org/docs/current/backup.html)
* [PostgreSQL - Add user to database](https://medium.com/coding-blocks/creating-user-database-and-adding-access-on-postgresql-8bfcd2f4a91e)

<style>
td, th {
   border: none!important;
}
</style>
| [<< PREVIOUS](index.html)|[NEXT >>](postgres-docker.html)|
|:----|----:|
| | |
