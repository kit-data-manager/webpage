---
title: Getting a Metadata Schema Record
breadcrumbs: /metastore/documentation/REST/Getting a Metadata Schema Record
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_doc_rest
---

# {{ page.title }}

For obtaining one metadata schema record you have to provide the value of the field 'schemaId'.

NOTE
: As 'Accept' field you have to provide 'application/vnd.datamanager.schema-record+json' otherwise you will
get the metadata schema instead.

{% capture my_include %}{% include_relative snippets/get-json-schema-record/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

In the actual HTTP request just access the path of the resource using the base path and the 'schemaid'. 
Be aware that you also have to provide the 'Accept' field.

{% capture my_include %}{% include_relative snippets/get-json-schema-record/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

As a result, you receive the metadata schema record send before and again the corresponding ETag in the HTTP response header. 

{% capture my_include %}{% include_relative snippets/get-json-schema-record/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

<style>
td, th {
   border: none!important;
}
</style>
|[PREVIOUS](register-schema.html)| [NEXT](get-schema-document.html) |
|:----|----:|
| | |

