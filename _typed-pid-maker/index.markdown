---
title: Typed PID Maker
breadcrumbs: /typed-pid-maker/
layout: default
description: A REST-Gateway to typed PIDs.
repository_url: https://github.com/kit-data-manager/pit-service
repository_name: kit-data-manager/pit-service
navigation_id: typed_pid_maker_index
tag-name: typed-pid-maker
---

# The {{ page.title }}

The Typed PID Maker is an entry point to integrate digital resources into the FAIR DO ecosystem.
It allows creating PIDs for resources and to provide them with the necessary metadata to ensure that the resources can be found and understood.

In order to do so, it requires access to a PID service.
It will then abstract away the complexity of these systems and provide a simple, unified REST interface for applications.
Via this interface, PIDs can be created, updated (maintained), resolved and validated.
Validation requires access to a public Data Type Registry (DTR), compatible with the ePIC DTR, which is pre-configured.
Creating and updating PIDs using the Typed PID Maker will always validate the PID records content before doing so.
Validation requires a PID Record to contain an attribute, indicating a Profile.
A Profile describes rules for the PID record, like mandatory and optional attributes.

If PID validation fails, the PID will not be created or updated to keep the quality of FAIR DOs high.
This is a huge benefit for research, as this ensures the FAIR DOs maintain a consistent quality and machine-actionability.
The REST interface eases the integration in arbitrary software systems.
Via the standardized AMQP protocol, created or modified PIDs can be distributed to other systems.

The system follows the [RDA Recommendations on PID Information Types](https://rd-alliance.org/group/pid-information-types-wg/outcomes/pid-information-types).

## Features

* Create, update/maintain and resolve PIDs
* Profile-based validation (implicit and explicit)
* Ease development by hiding complexity of PID Systems and Data Type Registries
* Common technologies for easy, programming language independent development (REST and JSON)
* Extendable to more PID Systems (by default only the Handle System is supported)
* (Optional) A sandboxed PID System for testing purposes
* (Optional) Notification of other systems about changes on PIDs via RabbitMQ (AMQP Standard)
* (Optional) JWT-based authentication and authorization via Keycloak

## Roadmap

Currently, the Typed PID Maker is in beta. While the development can be followed on GitHub, here are the most important points which have to be done before a 1.0 release:

* **Persist created PIDs locally.** – Ensure recoverability of PIDs in case all other systems fail.

* **Persist sandboxed PID Systems in a local database.** – Enable more extensive tests. Currently, the sandboxed PIDs are stored in memory (RAM).

* **Configurable Docker-Container for releases.** – Make it easier to try the service locally and ease the work of administrators as well.


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
