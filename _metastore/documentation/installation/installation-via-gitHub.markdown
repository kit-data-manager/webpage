---
title:  Installation via GitHub Packages
breadcrumbs: /metastore/documentation/installation/Installation via GitHub Packages
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_instal
---

# {{ page.title }} 
## Prerequisites
In order to run this microservice via docker you'll need:

* [Docker](https://www.docker.com/) 

## Installation
Typically, there is no need for locally building images as all version are accessible via GitHub Packages.
Have a look of available images and their tags [here](https://github.com/orgs/kit-data-manager/packages?repo_name=metastore2) 

## Create Docker Container
After you have chosen a suitable tag (latest should be fine in most cases) you have to create and start a docker
container for executing MetaStore as a service:
```
user@localhost:/home/user/metastore2$ docker run -d -p8040:8040 --name metastore4docker kitdm/metastore2:latest
57c973e7092bfc3778569f90632d60775dfecd12352f13a4fd2fdf4270865286
user@localhost:/home/user/metastore2$
```
## Setup MetaStore inside Docker
If you want to setup MetaStore inside a docker container you have stop and remove created image first and rebuild it with
mounting a local directory holding your 'application.properties'
```
user@localhost:/home/user/metastore2$ docker stop metastore4docker 
user@localhost:/home/user/metastore2$ docker rm metastore4docker 
user@localhost:/home/user/metastore2$ docker run -d -p8040:8040 \
                                                 --mount type=bind,source="$(pwd)"/config,target=/spring/metastore2/config \
                                                 --name metastore4docker kitdm/metastore2:latest
57c973e7092bfc3778569f90632d60775dfecd12352f13a4fd2fdf4270865286
user@localhost:/home/user/metastore2$
```
For how to set up MetaStore please refer to [Setup MetaStore](setup-metastore.html).

From now on the container has to be restarted to trigger new settings from 'application.properties'.
