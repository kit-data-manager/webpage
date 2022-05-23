---
title:  Build your own Docker Container
breadcrumbs: /metastore/documentation/installation
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_instal
---

# {{ page.title }} 
## Clone repository
First of all you'll have to clone this repository:
```
user@localhost:/home/user/$ git clone https://github.com/kit-data-manager/metastore2.git
Clone to 'metastore2'
[...]
user@localhost:/home/user/$ cd metastore2
user@localhost:/home/user/metastore2$
```

## Create Docker Image
Now you'll have to create an image containing the micro service. This can be done via a script.
On default the created images will be tagged as follows:

*'latest tag'-'actual date(yyyy-mm-dd)'* (e.g.: 1.0.0-SNAPSHOT-2022-05-23)

```
user@localhost:/home/user/metastore2$ bash docker/buildDocker.sh
---------------------------------------------------------------------------
Build docker container kitdm/metastore2:1.0.0-SNAPSHOT-2022-05-23
---------------------------------------------------------------------------
[...]
---------------------------------------------------------------------------
Now you can create and start the container by calling ...
---------------------------------------------------------------------------
user@localhost:/home/user/metastore2$
```

## Create Docker Container
After building image you have to create (and start) a container for executing microservice:
```
# If you want to use a specific image you may list all possible tags first.
user@localhost:/home/user/metastore2$ docker images kitdm/metastore2 --format {{.Tag}}
1.0.0-SNAPSHOT-2022-05-23
user@localhost:/home/user/metastore2$ docker run -d -p8040:8040 --name metastore4docker kitdm/metastore2:1.0.0-SNAPSHOT-2022-05-23
57c973e7092bfc3778569f90632d60775dfecd12352f13a4fd2fdf4270865286
user@localhost:/home/user/metastore2$
```

