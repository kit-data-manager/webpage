---
title: Getting a specific Version of Metadata Schema Document
breadcrumbs: /metastore/documentation/REST/Getting a Metadata Schema Document
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_doc_rest
---

# {{ page.title }}

To get a specific version of the metadata schema document just send an HTTP GET with the linked
'schemaId' and the version number you are looking for as query parameter: 

{% capture my_include %}{% include_relative snippets/get-json-schema-v1/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

HTTP-wise the call looks as follows: 

{% capture my_include %}{% include_relative snippets/get-json-schema-v1/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

As a result, you receive the initial XSD schema document (version 1). 

{% capture my_include %}{% include_relative snippets/get-json-schema-v1/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

NOTE
: Without the query paramter you will get the most recent version.

<style>
td, th {
   border: none!important;
}
</style>
|[<< PREVIOUS](list-specific-schema-records.html)| [NEXT >>](validate-metadata-document.html) |
|:----|----:|
| | |

