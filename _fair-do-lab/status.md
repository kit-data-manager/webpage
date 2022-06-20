---
title: FAIR DO Lab - status and stability
breadcrumbs: /typed-pid-maker/status
layout: default
description: API descriptions of the Labs components.
repository_url: https://github.com/kit-data-manager/testbed4inf
repository_name: kit-data-manager/testbed4inf
navigation_id: fair_do_lab_index
---

# {{ page.title }}

The following image describes the services, how they communicate, and their status. Not that some services, like RabbitMQ, Elasticsearch and Kibana are well-established components in modern infrastructures. The arrows describe dependencies: a service will not work properly if it points to a service which is missing. This should also help for the configuration of the FAIR DO Lab.

![status illustration of all components](../assets/images/fair-do-lab/status_components.drawio.svg)