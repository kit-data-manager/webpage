---
title:  Installation Elasticsearch (7.x)
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
: Right now only elasticsearch 7.x is supported by MetaStore.

--- 

You may need to install the apt-transport-https package on Debian before proceeding:
```
root@server:~# apt-get install apt-transport-https
```

Download and install the public signing key:

```
root@server:~# wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | gpg --dearmor -o /usr/share/keyrings/elasticsearch-keyring.gpg
```

Save the repository definition to /etc/apt/sources.list.d/elastic-7.x.list:

```
root@server:~# echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/7.x/apt stable main" | tee /etc/apt/sources.list.d/elastic-7.x.list
```
Final step: Install elasticsearch from registered repository
```
root@server:~# apt-get update && apt-get install elasticsearch
```

<style>
td, th {
   border: none!important;
}
</style>
| [<< PREVIOUS](setup-server.html)|[NEXT >>](manage-elasticsearch.html)|
|:----|----:|
| | |
