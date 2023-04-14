---
title:  Extend a Schema
breadcrumbs: /metastore/documentation/frontend
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_doc
---

# {{ page.title }} 
* Step 1: Fetch selected schema
* Step 2: Extend schema
* Step 3: Register new schema

---

## Step 1: Fetch selected schema
First of all the choosen schema has to be stored locally.
If the schema is already registered in the MetaStore please click
on the edit icon in the chosen row. Go to 'Schema Document' tab and edit the schema due to your needs.

### Example
Add the missing fields to the schema and mark them as 'required'.
Extend previous schema with a mandatory 'abstract' entry this would look like this:
```
{
    "$schema": "http://json-schema.org/draft-07/schema",
    "$id": "http://example.com/example.json",
    "type": "object",
    "title": "The root schema",
    "description": "The root schema comprises the entire JSON document.",
    "default": {},
    "examples": [
        {
            "author": "Last Name, First Name",
            "title": "My first document",
            "creation_date": "2022-04-11"
        }
    ],
    "required": [
        "author",
        "title",
        "creation_date"
    ],
    "properties": {
        "author": {
            "$id": "#/properties/author",
            "type": "string",
            "title": "Author:",
            "description": "The person who wrote the document.",
            "default": "",
            "examples": [
                "Last Name, First Name"
            ]
        },
        "title": {
            "$id": "#/properties/title",
            "type": "string",
            "title": "Title:",
            "description": "The title of the document.",
            "default": "",
            "examples": [
                "My first document"
            ]
        },
        "creation_date": {
            "$id": "#/properties/creation_date",
            "type": "string",
            "title": "Creation Date:",
            "description": "Creation date in the format 'YYYY-MM-DD'.",
            "default": "2022-01-01",
            "examples": [
                "2022-04-11"
            ]
        },
        "note": {
            "$id": "#/properties/note",
            "type": "string",
            "title": "Additional note:",
            "description": "Add some additional notes here. (optional)",
            "default": ""
        }
    },
    "additionalProperties": false
}
```
## Step 2: Create new schema
Register new version of schema by submitting it.

<style>
td, th {
   border: none!important;
}
</style>
| [<< PREVIOUS](register.html)|[NEXT >>](../metadata/introduction.html)|
|:----|----:|
| | |
