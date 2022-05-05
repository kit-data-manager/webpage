---
title: base-repo
breadcrumbs: /base-repo/
layout: default
description: A Generic, General Purpose Research Data Repository Service.
repository_url: https://github.com/kit-data-manager/base-repo
repository_name: kit-data-manager/base-repo
documentation_url: https://kit-data-manager.github.io/
navigation_id: base_repo_index
tag-name: base-repo
---

# The base-repo Service

The base-repo is a generic, general purpose research data repository service offering clear, machine-actionable RESTful interfaces for storing, retrieving and managing research data. Its purpose is to provide a low entrance barrier for research data management by keeping things as complex as necessary but as flexible as possible. Through the use of established technologies, i.e., software frameworks like Spring Boot, and broadly accepted standards, i.e., DataCite as base metadata standard, we provide a secure, maintainable and interoperable basis for entering the field of research data management.

## Features

* Light-weight microservice based on Spring Boot
* Easy installation, e.g., using available Docker images
* Full support of DataCite Standard 4.0
* Flexible organization of content in virtual folders
* Configurable versioning of metadata and content, e.g., following the OCFL specification
* (Optional) OAI-PMH support for metadata harvesting
* (Optional) Messaging support via RabbitMQ to process repository events, e.g., resource creation or file upload.
* (Optional) JWT-based authentication and authorization via Keycloak

## News

<ul>
  {% for post in site.posts %}
    {% if post.tags contains page.tag-name %}
      <li><a href="/webpage/{{ post.url }}">{{ post.title }}</a>, published {{ post.date | date: "%Y-%m-%d" }}</li>
    {% endif %}
  {% endfor %}
</ul>


