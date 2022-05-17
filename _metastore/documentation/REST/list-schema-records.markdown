---
title: Getting a List of Metadata Schema Records
breadcrumbs: /metastore/documentation/REST/Getting a Metadata Schema Document
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_doc_rest
---

# {{ page.title }}

Obtaining all accessible metadata schema records. 

{% capture my_include %}{% include_relative snippets/get-all-json-schemas/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

Same for HTTP request:

{% capture my_include %}{% include_relative snippets/get-all-json-schemas/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

As a result, you receive a list of metadata schema records. 

{% capture my_include %}{% include_relative snippets/get-all-json-schemas/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

NOTE
: Only the current version of each schemaId is listed.
: The header contains the field 'Content-Range" which displays delivered indices and the maximum number of available schema records. 
If there are more than 20 schemas registered you have to provide page and/or size as additional query parameters.

- page: Number of the page you want to get **(starting with page 0)**
- size: Number of entries per page.

The modified HTTP request  with pagination looks like follows:

{% capture my_include %}{% include_relative snippets/get-all-json-schemas-pagination/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}


<style>
td, th {
   border: none!important;
}
</style>
|[PREVIOUS](update-schema.html)| [NEXT](list-specific-schema-records.html) |
|:----|----:|
| | |

