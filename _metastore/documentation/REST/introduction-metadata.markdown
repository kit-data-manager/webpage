---
title: Metadata Management
breadcrumbs: /metastore/documentation/REST/Metadata Management
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_doc_rest
---

# {{ page.title }}

After registration of a schema metadata may be added to MetaStore.
In this section, the handling of metadata resources is explained. 
It all starts with creating your first metadata resource. The model of a metadata record looks
like this:

``` 
{
    "id": "...",
    "relatedResource": {
        "identifier": "...",
        "identifierType": "..."
    },
    "createdAt": "...",
    "lastUpdate": "...",
    "schema": {
        "identifier": "...",
        "identifierType": "..."
    },
    "schemaVersion": 1,
    "recordVersion": 1,
    "acl": [{
            "id": 3,
            "sid": "...",
            "permission": "..."
        }],
    "metadataDocumentUri": "...",
    "documentHash": "..."
}
``` 
At least the following elements are expected to be provided by the user: 

[point]
- schema: Identifier of the linked schema. (INTERNAL and URL supported as type)
- relatedResource: The link to the resource. 

In addition, ACL may be useful to make metadata editable by others. (This will be of interest while updating an existing metadata)

<style>
td, th {
   border: none!important;
}
</style>
|[<< PREVIOUS](validate-metadata-document.html)| [NEXT >>](register-metadata.html) |
|:----|----:|
| | |

