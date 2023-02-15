---
title:  Setup MetaStore Framework (Debian)
breadcrumbs: /metastore/documentation/installation
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_instal
---

# {{ page.title }} 
If you want to use also the search functionality you have to install the whole framework.
This includes:
- Indexing-Service
: Service to index created/updated metadata documents.

- ElasticSearch
: Service for searching metadata documents.

- RabbitMQ
: Messaging server to inform indexing-service about created/updated metadata documents.

This documents guides you to the several steps:
- [Installation Elasticsearch](setup-elasticsearch.html)
- [Installation RabbitMQ](setup-rabbitMq.html)
- [Installation Indexing-Service](setup-indexing.html)


<style>
td, th {
   border: none!important;
}
</style>
| |[NEXT >>](setup-elasticsearch.html)|
|:----|----:|
| | |
