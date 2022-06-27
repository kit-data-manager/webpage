---
title: Accessing Metadata Record
breadcrumbs: /metastore/documentation/REST/Accessing Metadata Record
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_doc_rest
---

# {{ page.title }}

For accessing the metadata record the same URL as before has to be used.
The only difference is the content type. It has to be set to "application/vnd.datamanager.metadata-record+json".
Then the command line looks like this:
{% capture my_include %}{% include_relative snippets/get-json-metadata-record/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

HTTP-wise the call looks as follows: 

{% capture my_include %}{% include_relative snippets/get-json-metadata-record/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

The linked metadata will be returned. The result is sent back to the user and will look that way:

{% capture my_include %}{% include_relative snippets/get-json-metadata-record/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

You also get the metadata record seen before.


<style>
td, th {
   border: none!important;
}
</style>
|[<< PREVIOUS](get-metadata-document.html)| [NEXT >>](update-metadata-record.html) |
|:----|----:|
| | |

