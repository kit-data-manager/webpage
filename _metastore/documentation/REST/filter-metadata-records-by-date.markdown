---
title: Filter Metadata Records by Date
breadcrumbs: /metastore/documentation/REST/Filter Metadata Records by Date
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_doc_rest
---

# {{ page.title }}

If you want to find all metadata records updated after a specific date.

Command line:
{% capture my_include %}{% include_relative snippets/find-json-metadata-record-from/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

HTTP-wise the call looks as follows: 

{% capture my_include %}{% include_relative snippets/find-json-metadata-record-from/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

You will get the current version metadata records updated ln the last 2 hours. 
{% capture my_include %}{% include_relative snippets/find-json-metadata-record-from/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

## Find in a specific date range
If you want to find all metadata records updated in a specific date range.

Command line:
{% capture my_include %}{% include_relative snippets/find-json-metadata-record-from-to/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

HTTP-wise the call looks as follows: 

{% capture my_include %}{% include_relative snippets/find-json-metadata-record-from-to/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

You will get an empty array as no metadata record exists in the given range:
{% capture my_include %}{% include_relative snippets/find-json-metadata-record-from-to/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}



<style>
td, th {
   border: none!important;
}
</style>
|[<< PREVIOUS](filter-metadata-records-by-related-resource.html)|  |
|:----|----:|
| | |

