---
title: FAIR DO Testbed
breadcrumbs: /testbed/
layout: default
description: A configurable FAIR DO blueprint architecture.
repository_url: https://github.com/kit-data-manager/testbed4inf
repository_name: kit-data-manager/testbed4inf
navigation_id: testbed_index
tag-name: testbed
---

# The {{ page.title }}

The {{ page.title }} is a configurable structure of services to fulfill generic FAIR Digital Object (FAIR DO) use cases. It is a proposal for research which can be configured and extended to specific needs. As the {{ page.title }} is easy to run on local computers and its default configuration offers a sandboxed PID service, it is therefore also suited to serve developers as a testing environment.

As its core, it uses the [Typed PID Maker], which then will notify other services about its actions, so they can automatically react to those. For example, an indexer service will put new or changed record information into a search engine without any human interaction required.

## Features

* All features of the [Typed PID Maker], including creation, updating and resolving PIDs
* Supporting development and training, due to its sandboxed default configuration
* Configurable services, which can be omitted if not required
* (Optional, default) Extendable architecture due to the established message broker "RabbitMQ", where services get all information about the situation
* (Optional, default) Automated indexing of PID records using Elasticsearch

## Roadmap

Currently, the {{ page.title }} contains services which are not production-ready. While the development can be followed on GitHub, here are the most important points which are planned in near future:

* The [Typed PID Maker] must reach version 1.0.

  Ideally, all services should be production-ready, but as the [Typed PID Maker] is a vital part of the {{ page.title }}, we consider its stability as a requirement for production use. As the {{ page.title }} is a living proposal, we do not have this requirement for all the services, but we offer [explicit documentation about the status of the different components](status.html).

* Stable and flexible indexing process.

  Searching for FAIR DOs is an important use case. We consider the current indexing process to be a proof-of-concept. For a 1.0 release, we plan to make it more flexible and use it to extract even more information about FAIR DOs.


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

[Typed PID Maker]: ../typed-pid-maker/
