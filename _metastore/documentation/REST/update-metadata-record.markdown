---
title: Updating a Metadata Record
breadcrumbs: /metastore/documentation/REST/Updating a Metadata Record (edit ACL entries)
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_doc_rest
---

# {{ page.title }}

The following example shows the update of the metadata record. As mentioned before the
ETag is needed:

``` 
metadata-record4json-v2.json:
{
    "relatedResource": {
        "identifier": "anyResourceId",
        "identifierType": "INTERNAL"
    },
    "schema": {
        "identifier": "my_first_json",
        "identifierType": "INTERNAL"
    },
    "schemaVersion": "2",
    "acl": [ {
      "id":null,
      "sid":"guest",
      "permission":"READ"
    } ]
}
``` 

``` 
metadata-v2.json:
{
"title": "My second JSON document",
"date": "2018-07-02"
}
``` 
{% capture my_include %}{% include_relative snippets/update-json-metadata-record-v2/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

You can see, that only the ACL entry for "guest" was added. All other properties are still the same. HTTP-wise the call looks as follows: 

{% capture my_include %}{% include_relative snippets/update-json-metadata-record-v2/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

You will get the new metadata record with the additional ACL entry. Version number of record was incremented by one and 'lastUpdate' was also modified by the server.
{% capture my_include %}{% include_relative snippets/update-json-metadata-record-v2/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

What you see is, that the metadata record looks different from the original document. 


<style>
td, th {
   border: none!important;
}
</style>
|[<< PREVIOUS](get-metadata-record.html)| [NEXT >>](find-metadata-records.html) |
|:----|----:|
| | |

