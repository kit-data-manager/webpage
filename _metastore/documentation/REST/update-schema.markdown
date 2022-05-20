---
title: Updating a Metadata Schema Document
breadcrumbs: /metastore/documentation/REST/Getting a Metadata Schema Document
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_doc_rest
---

# {{ page.title }}

NOTE
: Updating a metadata schema document will not break old metadata documents.
As every update results in a new version 'old' metadata schema documents are still 
available.

For updating an existing metadata schema (record) a valid ETag is needed. The actual ETag 
is available via the HTTP GET call of the metadata schema record. (see above)
Just send an HTTP POST with the updated metadata schema document and/or metadata schema record.

```
schema-v2.json:
{
    "$schema": "http://json-schema.org/draft/2019-09/schema#",
    "$id": "http://www.example.org/schema/json",
    "type": "object",
    "title": "Json schema for tests",
    "default": {},
    "required": [
        "title",
        "date"
    ],
    "properties": {
        "title": {
            "$id": "#/properties/string",
            "type": "string",
            "title": "Title",
            "description": "Title of object."
        },                                                                                                                                                                      
        "date": {
            "$id": "#/properties/string",
            "type": "string",
            "format": "date",
            "title": "Date",
            "description": "Date of object"
        }
    },
    "additionalProperties": false
} 
```

{% capture my_include %}{% include_relative snippets/update-json-schema-v2/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

HTTP-wise the call looks as follows: 

{% capture my_include %}{% include_relative snippets/update-json-schema-v2/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

As a result, you receive the updated schema record and in the HTTP response header
the new location URL and the ETag. 

{% capture my_include %}{% include_relative snippets/update-json-schema-v2/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}


<style>
td, th {
   border: none!important;
}
</style>
|[<< PREVIOUS](get-schema-document.html)| [NEXT >>](list-schema-records.html) |
|:----|----:|
| | |

