---
title: Getting a List of all Metadata Records
breadcrumbs: /metastore/documentation/REST/Getting a List of all Metadata Records
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_doc_rest
---

# {{ page.title }}

If you want to obtain all metadata records '/api/v1/metadata' endpoint has to be called. This may look like this:

{% capture my_include %}{% include_relative snippets/list-all-metadata-records/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

HTTP-wise the call looks as follows: 

{% capture my_include %}{% include_relative snippets/list-all-metadata-records/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

As a result, you receive a list of metadata records.

{% capture my_include %}{% include_relative snippets/list-all-metadata-records/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

<style>
td, th {
   border: none!important;
}
</style>
|[<< PREVIOUS](update-metadata-record.html)| [NEXT >>](filter-metadata-records-by-id.html) |
|:----|----:|
| | |

