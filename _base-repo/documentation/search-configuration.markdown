---
title:  "Configuration of Search Feature"
breadcrumbs: /base-repo/search-configuration
layout: default
description: A Generic, General Purpose Research Data Repository Service.
categories: base-repo general
repository_url: https://github.com/kit-data-manager/base-repo
repository_name: kit-data-manager/base-repo
navigation_id: base_repo_index
---

# {{ page.title }}

As of version 1.3.0 base-repo offers an integrated indexing and search for DataResources and its Contents. However, in order to be able to use the indexing and search, you need
to configure it in 'application.properties'. There, the following properties are available:

|property key|function|allowed values [default]
|----|----|----
|repo.search.enabled|Enables (true) or disables (false) indexing and search.|true or false [false]
|repo.search.url|The base URL of your Elastic installation | A URL containing protocol, hostname, and port [http://localhost:9200]
|repo.search.index|The search index queried by the search endpoint. The index filled by base-repo itself is called 'baserepo' and should always be listed in this property.|A single string denoting the queried index supporting wildcards and multi-index, e.g., index* or index1,index2 [baserepo]

Indexing and search is by default disabled, as it requires the installation of an Elastic search index, which can be obtained from the [official Webpage](https://www.elastic.co/de/downloads/elasticsearch).
If you like, also a dockerized Elastic instance can be used. 
As soon as Elastic is running, you can enable search and indexing by setting 'repo.search.enabled' to 'true' and providing the proper 'repo.search.url'. From now on, all
DataResources and their ContentInformation are also updated at the configured Elastic index if they are created, updated, or deleted. The Elastic index can either be 
searched via Elastic tools, e.g., [Kibana](https://www.elastic.co/de/kibana/) or via base-repo directly. Therefor, a new endpoint is offered available at '/api/v1/search'.
This endpoint accepts an Elastic query document and returns the query result in the official Elastic format. A sample call may look like: 

```bash
$ curl 'http://localhost:8080/api/v1/search' -i -X POST \
    -H 'Content-Type: application/json' \
    -d '{
    "query": {
        "bool": {
            "must": [
                {
                    "match_all": {}
                }
            ]
        }
    }
}'
```

## Search Security

Filling a search index with details about your base-repo contents may worry you a bit, as Elastic is typically used without any authentication or authorization. In order to cope
with this issue, we seamlessly integrated our own authentication and authorization into the search endpoint. If authentication is enabled for your base-repo instance, the user id
provided with the call to a base-repo endpoint is included into the search query automatically and will filter the results in a way that the caller only receives results 
on which (s)he has at least READ permissions. 

---
**NOTE**
Of course, returning results only readable by the caller just works via our search endpoint. Therefore, it is NOT recommended to make your Elastic instance publicly accessible,
as this would leverage this kind of authorization. 

---
