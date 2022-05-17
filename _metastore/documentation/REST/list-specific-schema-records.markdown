---
title: Getting a List of all Schema Records for a Specific SchemaId
breadcrumbs: /metastore/documentation/REST/Getting a Metadata Schema Document
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_doc_rest
---

# {{ page.title }}

If you want to obtain all versions of a specific schema you may add the schemaId as
a filter parameter. This may look like this:

{% capture my_include %}{% include_relative snippets/get-all-versions-of-a-json-schema/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

HTTP-wise the call looks as follows: 

{% capture my_include %}{% include_relative snippets/get-all-versions-of-a-json-schema/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

As a result, you receive a list of metadata schema records in descending order.
(current version first)

{% capture my_include %}{% include_relative snippets/get-all-versions-of-a-json-schema/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

<style>
td, th {
   border: none!important;
}
</style>
|[PREVIOUS](list-schema-records.html)| [NEXT](get-specific-schema-document.html) |
|:----|----:|
| | |

