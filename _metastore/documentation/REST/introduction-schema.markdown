---
title: Schema Registration and Management
breadcrumbs: /metastore/documentation/REST/introduction schema
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_doc_rest
---

# {{ page.title }}

In this first section, the handling of json schema resources is explained. It all starts with creating your first json schema resource. The model of a metadata schema record looks
like this:
``` json
{
  "schemaId" : "...",
  "schemaVersion" : 1,
  "mimeType" : "...",
  "type" : "...",
  "createdAt" : "...",
  "lastUpdate" : "...",
  "acl" : [ {
    "id" : 1,
    "sid" : "...",
    "permission" : "..."
  } ],
  "schemaDocumentUri" : "...",
  "schemaHash" : "...",
  "locked" : false
}
```
At least the following elements are expected to be provided by the user: 

- schemaId: A unique label for the schema.
- type: XML or JSON. For XSD schemas this should be 'XML'

In addition, ACL may be useful to make schema editable by others. (This will be of interest while updating an existing schema)

<style>
td, th {
   border: none!important;
}
</style>
|[<< PREVIOUS](index.html)| [NEXT >>](register-schema.html) |
|:----|----:|
| | |
