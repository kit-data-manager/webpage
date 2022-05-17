---
title: Register a schema
breadcrumbs: /metastore/documentation/REST/register schema
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_doc_rest
---

# {{ page.title }}

The following example shows the creation of the first json schema only providing mandatory fields mentioned above:
``` 
schema-record4json.json:
{
  "schemaId" : "my_first_json",
  "type" : "JSON"
}
```

```
schema.json:
{
  "$schema": "http://json-schema.org/draft/2019-09/schema#",
  "$id": "http://www.example.org/schema/json",
  "type": "object",
  "title": "Json schema for tests",
  "default": {},
  "required": [
      "title"
  ],
  "properties": {
    "title": {
      "$id": "#/properties/string",
      "type": "string",
      "title": "Title",
      "description": "Title of object."
    }
  },
  "additionalProperties": false
}
```

{% capture my_include %}{% include_relative snippets/register-json-schema/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

You can see, that most of the sent metadata schema record is empty. Only schemaId, mimeType and type are provided by the user. HTTP-wise the call looks as follows: 

{% capture my_include %}{% include_relative snippets/register-json-schema/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

As Content-Type only 'application/json' is supported and should be provided. The other headers are typically set by the HTTP client. After validating the 
provided document, adding missing information where possible and persisting the created resource, the result is sent back to the user and will look that way:

{% capture my_include %}{% include_relative snippets/register-json-schema/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

What you see is, that the metadata schema record looks different from the original document. All remaining elements received a value by the server. 
Furthermore, you'll find an ETag header with the current ETag of the resource. This value is returned by POST, GET and PUT calls and must be provided for 
all calls modifying the resource, e.g. POST, PUT and DELETE, in order to avoid conflicts.

<style>
td, th {
   border: none!important;
}
</style>
|[PREVIOUS](introduction-schema.html)| [NEXT](get-schema-record.html) |
|:----|----:|
| | |

