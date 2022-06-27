---
title: Getting a Metadata Schema Document
breadcrumbs: /metastore/documentation/REST/Getting a Metadata Schema Document
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_doc_rest
---

# {{ page.title }}

For obtaining accessible metadata schemas you also have to provide the 'schemaId'.
For accessing schema document you don't have to provide the 'Accept' header. 

{% capture my_include %}{% include_relative snippets/get-json-schema-document/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

In the actual HTTP request there is nothing special. You just access the path of the resource using the base path and the 'schemaId'.

{% capture my_include %}{% include_relative snippets/get-json-schema-document/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

As a result, you receive the XSD schema send before. 

{% capture my_include %}{% include_relative snippets/get-json-schema-document/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

<style>
td, th {
   border: none!important;
}
</style>
|[<< PREVIOUS](get-schema-record.html)| [NEXT >>](update-schema.html) |
|:----|----:|
| | |

