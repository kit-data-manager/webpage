---
title: Web Application Protocol Server
breadcrumbs: /wap-server/
layout: default
description: A service for annotating digital content.
navigation_id: wap-server_index
tag-name: wap-server
---

# The Web Application Protocol Server

This project provides a server for creating and managing annotations based on the [Web Annotation Data Model (WADM)](https://www.w3.org/TR/annotation-model/) 
implementing the complete [Web Annotation Protocol (WAP)](https://www.w3.org/TR/annotation-protocol/). The service is realized as microservice using Spring Boot 
and can be operated standalone for annotating arbitrary digital content. 

## Features

* Generic service for creating and managing annotations based on a standardized data model and access interface
* Fully based on RDF and therefore a first-class citizen in the linked (open) data world
* Query support either via RESTful endpoints or plain SPARQL queries
* Basic web interface with example data available

{% assign servicePosts = site.posts | where_exp: "post", "post.tags contains page.tag-name" %}
{% assign amountPosts = servicePosts | size %}
{% if amountPosts > 0 %}
## News

<ul>
  {% for post in servicePosts %}
      <li><a href="/webpage/{{ post.url }}">{{ post.title }}</a>, published {{ post.date | date: "%Y-%m-%d" }}</li>
  {% endfor %}
</ul>
{% endif %}
