---
title: Metadata Editor
breadcrumbs: /metadata-editor/
layout: default
description: A JavaScript library to generate Web Forms for your Metadata.
repository_url: https://github.com/kit-data-manager/metadata-editor
repository_name: kit-data-manager/metadata-editor
navigation_id: metadata_editor_index
tag-name: metadata-editor
---

# The Metadata Editor

The Metadata Editor is a JavaScript library allowing to generate web forms and validate metadata in an intuitive and 
generic way with the help of [JSON Form Library](https://github.com/jsonform/jsonform/wiki). 
Moreover, it enables to list various resources given by the user as a JSON object. In addition, the editor offers the possibility 
to the developer to add different icons in order to perform 
CRUD (Create, Read, Update, Delete) operations. In order to support the JSON Schema draft-2019-09, [Ajv JSON Schema Validator](https://ajv.js.org/) 
has been integrated in the JSON Form Library.

## Features

* Intuitive and generic generation of forms based on given JSON Schemas provided by the developer
* Support for standalone-forms and tabular listings of multiple resources
* Validation of JSON resources
* Full support of JSON Form Library and Tabulator Library features
* Easy to implement, callback-based integration of backend services


## News

<ul>
  {% for post in site.posts %}
    {% if post.tags contains page.tag-name %}
      <li><a href="/webpage/{{ post.url }}">{{ post.title }}</a>, published {{ post.date | date: "%Y-%m-%d" }}</li>
    {% endif %}
  {% endfor %}
</ul>


