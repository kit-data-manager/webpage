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

<p class="align-middle items-center">The Typed PID Maker is an entry point to integrate digital resources into the FAIR Digital Object (FAIR DO) ecosystem.
It allows creating PIDs for resources and to provide them with the necessary metadata to ensure that the resources can be found and understood.
As a result, a machine-readable representation of all kinds of research artifacts allows act on such FAIR Digital Objects 
which present themselves as PID, e.g., <pid-component value='21.11152/6ea60288-d895-414e-80c0-26c9fdd662b2'></pid-component>, 
but carry much more than just a pointer to a landing page.</p>

In order to do so, it requires write-access to a PID service (sometimes called a "Prefix").
It will then abstract away the complexity of such systems and provide a simple, unified REST interface for applications.
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

* Create PIDs containing typed key-value-pairs for easy, fast, and automated decision-making
* Maintain the information within these PIDs
* Validate PIDs (Profile-based validation)
* Resolve PIDs
* Store the created PIDs in your database and query them
* Build & use your own search index: Search for information stored within PIDs
* Ease development by hiding complexity of PID Systems and Data Type Registries
* Common technologies for easy, programming language independent development (REST and JSON)
* Extendable to more PID Systems (currently only supports the Handle System)
* Bootstrap with existing PIDs in a PID Prefix
* Extract all PIDs to a CSV file
* (Optional) Sandboxed PID Systems for testing purposes (in-memory or database)
* (Optional) Notification of other systems about changes on PIDs via RabbitMQ (AMQP Standard)
* (Optional) Authentication via [JWT](https://jwt.io/introduction) or [KeyCloak](https://www.keycloak.org/)
* Make your PIDs distinguishable with a customizable branding-prefix and other customization options

## Roadmap

The Typed PID Maker is stable and production-ready. The banner at the top shows the current version. Besides maintenance, there are further plans (excerpt/directions):

* **Ease deployment** – Make it easier to try the service locally and ease the work of administrators as well. For example by offering a configurable docker container. [#25](https://github.com/kit-data-manager/pit-service/issues/25)
* **Different enhancements regarding PID resolution and maintenance** – The Typed PID Maker is also easing the maintenance of FAIR DOs. We collect and evaluate such [enhancements in our issue tracker](https://github.com/kit-data-manager/pit-service/issues?q=is%3Aissue+is%3Aopen+label%3Aenhancement).


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
