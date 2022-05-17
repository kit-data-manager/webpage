---
title: MetaStore
breadcrumbs: /metastore/
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
documentation_url: https://kit-data-manager.github.io/
navigation_id: metastore_index
tag-name: metastore
---

# The MetaStore Service

The MetaStore is a generic, general metadata repository and schema registry 
service offering clear, machine-actionable RESTful interfaces for storing, 
retrieving and managing metadata documents and its related schemas. 
Its purpose is to provide a low entrance barrier for research data management 
by keeping things as complex as necessary but as flexible as possible. 


## Features

* Low-threshold access due to simple user interface.
* Light-weight microservice based on [Spring Boot](https://spring.io/projects/spring-boot)
* Easy installation, e.g., using available [Docker images](https://hub.docker.com/r/kitdm/metastore2)
* Versioning (history) of metadata and schema documents
* (Optional) OAI-PMH support for metadata harvesting
* (Optional) Messaging support via [RabbitMQ](https://www.rabbitmq.com/) to process repository events, e.g., resource creation or file upload.
* (Optional) JWT-based authentication and authorization via Keycloak

<div class="flex flex-wrap -m-3 inset-5px">
        <div class="w-full sm:w-1/2 md:w-1/3 flex-col p-3">
            <h1 class="text-center"><i class="fa-brands fa-docker" aria-hidden="true"></i></h1>
            <h3 class="text-center">Quickstart</h3>
            <p>In case you want to have a quick try of base-repo without any configuration effort, check out our <a href="https://hub.docker.com/r/kitdm/metastore2/tags">Docker Images</a>.
                You'll get a pre-configured instance which can be customized later on according to your preferences.
            </p>
        </div>
        <div class="w-full sm:w-1/2 md:w-1/3 flex-col p-3">
            <h1 class="text-center"><i class="fa-solid fa-circle-question" aria-hidden="true"></i></h1>
            <h3 class="text-center">Further Reading</h3>
            <p>If you want to read more before you give MetaStore a try, check out the different documents grouped by audience. There you can learn more about the
            <a href="/webpage/metastore/documentation/api-docs.html">RESTful API</a>, the <a href="/webpage/metastore/documentation/index.html">Usage</a>, or the <a href="/webpage/metastore/documentation/installation.html">Installation</a>.
            </p>
        </div>
        <div class="w-full sm:w-1/2 md:w-1/3 flex-col p-3">
            <h1 class="text-center"><i class="fa fa-code-fork" aria-hidden="true"></i></h1>
            <h3 class="text-center">Looking for Code?</h3>
            <p>In case you are interested in source-code, check out the <a href="https://github.com/kit-data-manager/metastore2">GitHub Repository of MetaStore</a>. There
            you can also open an <a href="https://github.com/kit-data-manager/metastore2/issues">Issue</a> to report a bug or to request a new feature.</p>
        </div>
</div>



## News

<ul>
  {% for post in site.posts %}
    {% if post.tags contains page.tag-name %}
      <li><a href="/webpage/{{ post.url }}">{{ post.title }}</a>, published {{ post.date | date: "%Y-%m-%d" }}</li>
    {% endif %}
  {% endfor %}
</ul>


