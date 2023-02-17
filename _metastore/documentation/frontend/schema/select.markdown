---
title:  Select a Schema
breadcrumbs: /metastore/documentation/frontend
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_doc
---

# {{ page.title }} 
Before starting ingesting metadata documents in MetaStore an appropriate schema 
should be selected. To do this, some fundamental decisions must be made.

---

## Ingredients

- (local) MetaStore instance
- Web Browser

---

## Work Steps (Summary)

### Select/create a Schema
* Step 1: Which metadata do I need?
* Step 2: Search for existing metadata standards
* Step 3: Create your own schema (optional)

---

## Step 1: Which metadata do I need?
Metadata should describe the associated data in such a way that it can be 
intrepreted without further information and also reproduced if necessary. 
First of all identified metadata entries should be collected. 


## Step 2: Search for existing metadata standards
In most cases there is already at least one schema document fulfilling your needs
containing all entries collected in beforehand.

But how to find this schema?

The Metadata Standards Catalog may be a good starting point. There exists 
several instances:
- [https://rdamsc.bath.ac.uk/](https://rdamsc.bath.ac.uk/)
- [https://msc.datamanager.kit.edu/](https://msc.datamanager.kit.edu/)

There may be other catalogs related to a specific domain.

***NOTE:*** Not all schemas listed there might fit to MetaStore as MetaStore only 
supports JSON Schema and XML Schema. 

If there is no schema fulfilling your needs look for the schema document fitting 
best and extend the given schema. (See ['Extend an existing schema document'](./extend.html))

## Step 3: Create your own schema (optional)
If there is really no fitting schema a new schema has to be created.

There are two possibilities:
- [JSON Schema](https://json-schema.org/)
- [XML Schema](https://www.w3schools.com/XML/schema_howto.asp)

If you are already familiar with one of these two possibilities you should use 
this. Otherwise, you should use JSON Schema as it is easier to create and is supported
out of the box by the GUI delivered with MetaStore. 

There are several tools for creating a schema from scratch:
- JSON Schema
  - [https://www.jsonschema.net/home](https://www.jsonschema.net/home)
  - [https://www.liquid-technologies.com/online-json-to-schema-converter](https://www.liquid-technologies.com/online-json-to-schema-converter)
  - [https://app.quicktype.io/#l=schema](https://app.quicktype.io/#l=schema)
  - [...](https://json-schema.org/implementations.html#schema-generators)
- XML Schema
  - [https://www.xmlfox.com/](https://www.xmlfox.com/)
  - [https://www.liquid-technologies.com/xml-schema-editor](https://www.liquid-technologies.com/xml-schema-editor) (commercial)
  - [https://www.oxygenxml.com/xml_editor/xml_schema_editor.html](https://www.oxygenxml.com/xml_editor/xml_schema_editor.html)(commercial)
  - [...](https://www.w3.org/XML/Schema#Tools)

Let's start with a simple JSON Schema containing 
- author
- title
- creation date

The JSON document may look like this:
```
{
  "author": "Last Name, First Name",
  "title": "My first document",
  "creation_date": "2022-04-11"
}
```
This example results in the following schema using the first link given above:
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
        }
    },
    "additionalProperties": false
}
```
***Note:*** The following JSON Schema specifications are supported by the library used:
* Draft v7 
* Draft v2019-09

### Recommendations for JSON Schemas
If the scientists will later use the web interface to store their metadata 
documents, here are a few hints to make their work a little easier. 
As the web interface uses the entries from the schema to create a form from them, 
some fields should be filled with meaningful values.
Each property of the schema contains some optional entries:
1. title - The text of the title will be displayed above the input field.
2. description - The text of the description will be displayed below the input 
   field and should contain some additional infos.
3. default - The input field will be prefilled with the default value. This might
   be helpful if a field mostly contains a fixed value. 
4. enum - Defines an array of possible values which is displayed as a dropdown menu.

The entry 'additionalProperties' at the end of the schema should be always 'false' 
to forbid custom entries.

<style>
td, th {
   border: none!important;
}
</style>
| [<< PREVIOUS](introduction.html)|[NEXT >>](register.html)|
|:----|----:|
| | |
