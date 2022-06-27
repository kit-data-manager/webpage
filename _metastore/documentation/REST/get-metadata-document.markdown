---
title: Accessing Metadata Document
breadcrumbs: /metastore/documentation/REST/Accessing Metadata Document
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_doc_rest
---

# {{ page.title }}

For accessing the metadata the location URL provided before may be used.
The URL is compiled by the id of the metadata and its version.
{% capture my_include %}{% include_relative snippets/get-json-metadata-document/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

HTTP-wise the call looks as follows: 

{% capture my_include %}{% include_relative snippets/get-json-metadata-document/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

The linked metadata will be returned. The result is sent back to the user and will look that way:

{% capture my_include %}{% include_relative snippets/get-json-metadata-document/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

What you see is, that the metadata is untouched.

<style>
td, th {
   border: none!important;
}
</style>
|[<< PREVIOUS](register-metadata.html)| [NEXT >>](get-metadata-record.html) |
|:----|----:|
| | |

