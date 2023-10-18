---
title:  "Introduction of Messaging Feature"
breadcrumbs: /metastore/documentation/installation/messaging/introduction
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
categories: metastore messaging
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_instal
---

# {{ page.title }}

For MetaStore creating a schema and managing linked metadata documents is only the simplest workflow. In many cases, additional steps have to be performed in order to obtain all required information, to index metadata documents or to monitor what happens. For this purpose, MetaStore offers a feature called 'messaging' emitting small messages after creation, update or deletion of a metadata document has succeeded. The following chapters describe how these messages 
are look like, when they are emitted and how to deal with them in order to react on certain repository events.

<style>
td, th {
   border: none!important;
}
</style>
| [<< PREVIOUS](../index.html)|[NEXT >>](messaging-types-formats.html)|
|:----|----:|
| | |
