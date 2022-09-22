---
title: Collection Registry
breadcrumbs: /collection-registry/
layout: default
description: A General Purpose Service for building Research Data Collections.
repository_url: https://github.com/kit-data-manager/collection-api
repository_name: kit-data-manager/collection-api
navigation_id: collection_registry_index
tag-name: collection-registry
---

# The Collection Registry

The Collection Registry allows building collections of digital objects, independent of any repository in order to facilitate data 
interoperability, reuse and make collections actionable to be able to cope with ever-increasing amounts and volumes of data.
The Collection Registry has been proposed by the [RDA Recommendation on Research Data Collections](https://zenodo.org/record/2428145#.X0YVOpMzafU)
and has been implemented following these recommendations. 

## Features

* Light-weight microservice based on Spring Boot
* Easy installation, e.g., using available Docker images
* Full implementation of the official RDA recommendation on Research Collections
* Support for typed collections 
* (Optional) PID support for collections and their members
* Smart-Collections for rule-based grouping of member items

## News

<ul>
  {% for post in site.posts %}
    {% if post.tags contains page.tag-name %}
      <li><a href="/webpage/{{ post.url }}">{{ post.title }}</a>, published {{ post.date | date: "%Y-%m-%d" }}</li>
    {% endif %}
  {% endfor %}
</ul>


