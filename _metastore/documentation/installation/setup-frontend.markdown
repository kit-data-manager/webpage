---
title:  Install MetaStore Frontend
breadcrumbs: /metastore/documentation/installation
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_instal
---

# {{ page.title }} 

## Requirements
- Apache2
- Git

## Build Indexing-Service
The first step is to download the repository from git:
```
user@server:~# git clone https://github.com/kit-data-manager/frontend-collection.git
Cloning into 'frontend-collection'...
remote: Enumerating objects: 1437, done.
remote: Counting objects: 100% (329/329), done.
remote: Compressing objects: 100% (214/214), done.
remote: Total 1437 (delta 201), reused 212 (delta 115), pack-reused 1108
Receiving objects: 100% (1437/1437), 10.75 MiB | 7.28 MiB/s, done.
Resolving deltas: 100% (616/616), done.
user@server:~# cd frontend-collection/
```
Checkout branch 'docker-metastore' to reduce configuration effort.
```
user@server:~/frontend-collection# git checkout docker-metastore
Branch 'docker-metastore' set up to track remote branch 'docker-metastore' from 'origin'.
Switched to a new branch 'docker-metastore'
user@server:~/frontend-collection# 
```
Setup frontend for specific server. Edit 'js/metastore.settings.js'.
It may look like this:
```
export let ajaxBaseUrl = "https://'FQDN'/api/v1/";

export const keycloak = undefined;

export const showServiceUrl = false;

export const appDescription = {
    "app-logo":"./images/metadata.jpg",
    "app-title":"MetaStore Frontend 4 Docker",
    "app-subtitle":"Schema and Metadata Management"
};
```
--- 
NOTE
: Replace ***'FQDN'*** by the fully qualified hostname of your MetaStore Server.(e.g.: export let ajaxBaseUrl = "https://www.example.org/api/v1";)
: If you are using a proxy, there is no need for a port.

--- 

Copy all files to apaches 'DocumentRoot' you may have configured in beforehand. (Default: /var/www/html)
```
user@server:~/frontend-collection# sudo cp -R ../frontend-collection/ /var/www/'FQDN'/frontend
```
Check installation:
Use your favourite browser to go to http(s)://'FQDN'/frontend.
If you see the schema management page without any errors, everything is fine.:-)

Congratulations: You are done! 
    
<style>
td, th {
   border: none!important;
}
</style>
| [<< PREVIOUS](setup-apache-as-proxy.html) ||
|:----|----:|
| | |
