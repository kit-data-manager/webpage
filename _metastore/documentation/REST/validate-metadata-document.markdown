---
title: Validating Metadata Document
breadcrumbs: /metastore/documentation/REST/Validating Metadata Document
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_doc_rest
---

# {{ page.title }}

Before an ingest of metadata is made the metadata should be successfully validated. Otherwise 
the ingest may be rejected. Select the schema and the schemaVersion to validate given document.

``` 
metadata-v2.json:
{
"title": "My third JSON document",
"date": "2018-07-02"
}
``` 

On a first step validation with the old schema will be done:

{% capture my_include %}{% include_relative snippets/validate-json-document-v1/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

Same for the HTTP request. The schemaVersion number is set by a query parameter.

{% capture my_include %}{% include_relative snippets/validate-json-document-v1/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

As a result, you receive 422 as HTTP status and an error message holding some information about the error.
(Unfortunately not documented here due to technical reasons.)

{% capture my_include %}{% include_relative snippets/validate-json-document-v1/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

The document holds a mandatory field introduced in the second version of schema.
Let's try to validate with second version of schema. Only version number will be different. (if no query
parameter is available the current version will be selected)

{% capture my_include %}{% include_relative snippets/validate-json-document-v2/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

Same for the HTTP request.

{% capture my_include %}{% include_relative snippets/validate-json-document-v2/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

Everything should be fine now. As a result, you receive 204 as HTTP status and no further content. 

{% capture my_include %}{% include_relative snippets/validate-json-document-v2/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

<style>
td, th {
   border: none!important;
}
</style>
|[<< PREVIOUS](get-specific-schema-document.html)| [NEXT >>](introduction-metadata.html) |
|:----|----:|
| | |

