---
title: Filter Metadata Records by Id
breadcrumbs: /metastore/documentation/REST/Filter Metadata Records by Id
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_doc_rest
---

# {{ page.title }}

If you want to obtain all versions of a specific resource you may add 'id' as
a filter parameter. This may look like this:

{% capture my_include %}{% include_relative snippets/list-all-versions-of-json-metadata-document/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

HTTP-wise the call looks as follows: 

{% capture my_include %}{% include_relative snippets/list-all-versions-of-json-metadata-document/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

As a result, you receive a list of metadata records in descending order.
(current version first)

{% capture my_include %}{% include_relative snippets/list-all-versions-of-json-metadata-document/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

<style>
td, th {
   border: none!important;
}
</style>
|[<< PREVIOUS](find-metadata-records.html)| [NEXT >>](filter-metadata-records-by-related-resource.html) |
|:----|----:|
| | |

