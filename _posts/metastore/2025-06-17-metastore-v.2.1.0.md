---
breadcrumbs: /metastore/news/
layout: default
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
documentation_url: https://kit-data-manager.github.io/
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
no_nav: true
tags: metastore
title:  "MetaStore v2.1.0 released"
---

Today, we like to announce version 2.1.0 of the MetaStore service. Below, you can find the list of changes. 

## New Features
* Add actuator endpoint for prometheus metrics.

## Bugfixes
* Fix broken docker image due to incompatible dependencies.

## Dependency Upgrades
* Update dependency gradle to v8.14.2
* Update dependency io.micronaut.micrometer:micronaut-micrometer-registry-prometheus to v5.11.0
* Update dependency org.apache.tika:tika-core to v3.2.0
* Update dependency org.mockito:mockito-core to v5.18.0
* Update dependency org.postgresql:postgresql to v42.7.7
* Update dependency org.springframework.boot:spring-boot-starter-actuator to v3.5.0
* Update dependency org.springframework.cloud:spring-cloud-starter-netflix-eureka-client to v4.3.0
* Update dependency org.springframework.data:spring-data-elasticsearch to v5.5.1
* Update dependency org.springframework.restdocs:spring-restdocs-mockmvc to v3.0.4
* Update dependency org.springframework:spring-messaging to v6.2.8Update springDocVersion to v2.8.9
* Update plugin org.owasp.dependencycheck to v12.1.3
* Update plugin org.springframework.boot to v3.5.0

If you face any issues, please file an [issue at GitHub](https://github.com/kit-data-manager/metastore2/issues). 

