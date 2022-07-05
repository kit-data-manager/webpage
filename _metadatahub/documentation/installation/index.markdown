---
title:  Installation
breadcrumbs: /metadatahub/documentation/installation
layout: default
description: A generic metadata repository for all kind of metadata repositories.
repository_url: https://git.rwth-aachen.de/nfdi4ing/s-3/s-3-3/metadatahub
repository_name: nfdi4ing/s-3/s-3-3/metadatahub
documentation_url: https://kit-data-manager.github.io/
---

# {{ page.title }} 
## Prerequisites
In order to run this microservice you'll need:

* Linux, MacOs, WSL (not tested) 
* [Java SE Development Kit >=8 and <=17](https://openjdk.java.net/) 
* [git](https://git-scm.com/) 

## Installation
### Clone repository
First of all you'll have to clone this repository:
```
user@localhost:/home/user/$ git clone https://git.rwth-aachen.de/nfdi4ing/s-3/s-3-3/metadatahub
Clone to 'metastore2'
[...]
user@localhost:/home/user/$ cd metadatahub
user@localhost:/home/user/metadatahub$
```
### Build service 
To build service just execute the build.sh script:
```
user@localhost:/home/user/metadatahub$bash build.sh /PATH/TO/EMPTY/INSTALLATION/DIRECTORY [FQDN|localhost]
---------------------------------------------------------------------------
Build microservice of metastore2 at /PATH/TO/EMPTY/INSTALLATION/DIRECTORY
---------------------------------------------------------------------------
[...]
---------------------------------------------------------------------------
Now you can start the service by calling /PATH/TO/EMPTY/INSTALLATION/DIRECTORY/run.sh
---------------------------------------------------------------------------
user@localhost:/home/user/metadatahub$
```
: FQDN
  Full qualified domain name (e.g.: metadatahub.example.com)
  
To use your own mappings you have to remove all mappings (*_mappings.json) from the 'mappings' subdirectory and 
replace it by your own. 
The JSON files have to be valid against 
[this schema](https://git.rwth-aachen.de/nfdi4ing/s-3/s-3-3/metadatahub/-/blob/main/src/main/resources/json/schema/http_mapping.json).

### Installation (Docker)
If you want to use a Docker image please refer to [this documentation](https://git.rwth-aachen.de/nfdi4ing/s-3/s-3-3/metadatahub/-/tree/main/#dockerize-service).

