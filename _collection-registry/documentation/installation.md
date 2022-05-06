---
title: Installation
breadcrumbs: /collection-registry/documentation/
layout: default
description: A General Purpose Service for building Research Data Collections.
repository_url: https://github.com/kit-data-manager/collection-api
repository_name: kit-data-manager/collection-api
navigation_id: collection_registry_index
---

# How to start

For running the Collection Registry you may either use a docker container or you build and run the service from source.
The source code is available at [GitHub](https://github.com/kit-data-manager/collection-api). For more information about 
compiling and starting from source, please refer to the README located in the source repository.

In the following, running the Collection Registry using docker is explained.

## Prerequisites

* docker (tested with 19.03.8).

## Startup

```shell
$ docker run -d -p 8080:8080 kitdm/collection-api:latest

Unable to find image 'kitdm/collection-api:latest' locally
latest: Pulling from kitdm/collection-api
3192219afd04: Pull complete
17c160265e75: Pull complete
cc4fe40d0e61: Pull complete
9d647f502a07: Pull complete
[...]
Status: Downloaded newer image for kitdm/collection-api:latest
```

As soon as the microservice is started, you can browse to http://localhost:8080/swagger-ui.html in order test that the service works.
