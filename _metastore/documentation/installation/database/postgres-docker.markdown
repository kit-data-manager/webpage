---
title:  Installation PostgreSQL (Docker)
breadcrumbs: /metastore/documentation/installation/database/Installation PostgreSQL (Docker)
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_instal
---

# {{ page.title }} 
Installation PostgreSQL

## Prerequisites
- Docker version 18.06 or higher

## Build and start docker container with postgreSQL
First time you have to build docker container. Port 5555 is used to avoid overlap.
```bash=bash
# Create directory for database dumps
user@localhost:/home/user/$mkdir -p /path/for/backups/postgres
user@localhost:/home/user/$docker run -p 5555:5432 --name postgres4metastore -e POSTGRES_PASSWORD=YOUR_ADMIN_PASSWORD -v /path/for/backups/postgres:/dump -d postgres
123.....
```
Now postgreSQL is available on localhost via port 5555.

## Setup Database
```bash=bash
user@localhost:/home/user/$docker exec -ti postgres4metastore sh -c "psql postgres -h localhost -d postgres"
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
Now postgreSQL is setup for metastore2.

To start/stop docker container afterwards use
```bash=bash
user@localhost:/home/user/$docker stop postgres4metastore
user@localhost:/home/user/$docker start postgres4metastore
```
## Backup PostgreSQL
```bash=bash
# Backup metastore
user@localhost:/home/user/$docker exec -ti postgres4metastore sh -c "pg_dump -U postgres -h 127.0.0.1 metastore > /dump/database_dump_metastore_`date +%Y_%m_%dt%H_%M`.sql"
```

