---
breadcrumbs: /metastore/search-configuration
layout: default
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
documentation_url: https://kit-data-manager.github.io/
description: A Research Data Repository Service for Managing Metadata Documents>
categories: metastore general
title:  "Configuration of Search Feature"
navigation_id: metastore_doc
---

# {{ page.title }}

As of version 1.2.0 MetaStore offers an integrated indexing and search for metadata documents and its records. However, in order to be able to use the indexing and search, you need
to configure it in 'application.properties'. There, the following properties are available:

|property key|function|allowed values [default]
|----|----|----
|repo.search.enabled|Enables (true) or disables (false) indexing and search.|true or false [false]
|repo.search.url|The base URL of your Elastic installation | A URL containing protocol, hostname, and port [http://localhost:9200]

Indexing and search is by default disabled, as it requires the installation of an Elastic search index, which can be obtained from the [official Webpage](https://www.elastic.co/de/downloads/elasticsearch).
If you like, also a dockerized Elastic instance can be used. 
As soon as Elastic is running, you can enable search and indexing by setting 'repo.search.enabled' to 'true' and providing the proper 'repo.search.url'. From now on, all
metadata documents and their records are also updated at the configured Elastic index if they are created, updated, or deleted. The Elastic index can either be 
searched via Elastic tools, e.g., [Kibana](https://www.elastic.co/de/kibana/) or via base-repo directly. Therefor, a new endpoint is offered available at '/api/v1/search'.
This endpoint accepts an Elastic query document and returns the query result in the official Elastic format. A sample call may look like: 

```bash
$ curl 'http://localhost:8080/api/v1/metadata/search' -i -X POST \
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

Filling a search index with details about your MetaStore contents may worry you a bit, as Elastic is typically used without any authentication or authorization. In order to cope
with this issue, we seamlessly integrated our own authentication and authorization into the search endpoint. If authentication is enabled for your MetaStore instance, the user id
provided with the call to a base-repo endpoint is included into the search query automatically and will filter the results in a way that the caller only receives results 
on which (s)he has at least READ permissions. 

---
**NOTE**
Of course, returning results only readable by the caller just works via our search endpoint. Therefore, it is NOT recommended to make your Elastic instance publicly accessible,
as this would leverage this kind of authorization. 

---
