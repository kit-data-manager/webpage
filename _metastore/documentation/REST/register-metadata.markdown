---
title: Register/Ingest a Metadata Record with Metadata Document
breadcrumbs: /metastore/documentation/REST/Ingest a Metadata Record with Metadata Document
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_doc_rest
---

# {{ page.title }}

The following example shows the creation of the first metadata record and its metadata only providing mandatory fields mentioned above:

``` 
metadata-record4json.json:
{
    "relatedResource": {
        "identifier": "anyResourceId",
        "identifierType": "INTERNAL"
    },
    "schema": {
        "identifier": "my_first_json",
        "identifierType": "INTERNAL"
    },
    "schemaVersion": 1
}
``` 

``` 
metadata.json:
{
  "title": "My first JSON document"
}
``` 
The schemaId used while registering metadata schema has to be used to link the metadata with the
approbriate metadata schema.
{% capture my_include %}{% include_relative snippets/ingest-json-metadata-document/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

You can see, that most of the sent metadata schema record is empty. Only schemaId and relatedResource are provided by the user. HTTP-wise the call looks as follows: 

{% capture my_include %}{% include_relative snippets/ingest-json-metadata-document/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

As Content-Type only 'application/json' is supported and should be provided. The other headers are typically set by the HTTP client. After validating the 
provided document, adding missing information where possible and persisting the created resource, the result is sent back to the user and will look that way:

{% capture my_include %}{% include_relative snippets/ingest-json-metadata-document/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

What you see is, that the metadata record looks different from the original document. All remaining elements received a value by the server. 
In the header you'll find a location URL to access the ingested metadata and an ETag with the current ETag of the resource. This value is returned by POST, GET and PUT calls and must be provided for 
all calls modifying the resource, e.g. POST, PUT and DELETE, in order to avoid conflicts.


<style>
td, th {
   border: none!important;
}
</style>
|[<< PREVIOUS](introduction-metadata.html)| [NEXT >>](get-metadata-document.html) |
|:----|----:|
| | |

