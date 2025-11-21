---
breadcrumbs: /metastore/news/
layout: default
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
documentation_url: https://kit-data-manager.github.io/
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
no_nav: true
tags: metastore
title:  "MetaStore v2.1.1 released"
---

Today, we like to announce version 2.1.1 of the MetaStore service. Below, you can find the list of changes. 

## Bugfixes
* Fix bug while migrating to v2.x.x, which breaks when revoked records are available.

## New Features
* Add property 'repo.monitoring.serviceName' to set the name of the service for monitoring.

## Changed
* Move parts of monitoring to repo-core -> Change in configuration:
    - `metastore.monitoring.enabled` -> `repo.monitoring.enabled`
    - `metastore.monitoring.noOfDaysToKeep` -> `repo.monitoring.noOfDaysToKeep`

## Dependency Upgrades
* Update actions/checkout action to v5
* Update dependency com.google.errorprone:error_prone_core to v2.41.0
* Update dependency com.networknt:json-schema-validator to v1.5.8
* Update dependency commons-io:commons-io to v2.20.0
* Update dependency gradle to v9
* Update dependency io.micronaut.micrometer:micronaut-micrometer-registry-prometheus to v5.12.0
* Update dependency org.apache.commons:commons-text to v1.14.0
* Update dependency org.apache.tika:tika-core to v3.2.2
* Update dependency org.mockito:mockito-core to v5.19.0
* Update dependency org.springframework:spring-messaging to v6.2.10
* Update dependency org.springframework.boot:spring-boot-starter-actuator to v3.5.4
* Update dependency org.springframework.data:spring-data-elasticsearch to v5.5.3
* Update javersVersion
* Update plugin com.gorylenko.gradle-git-properties to v2.5.2
* Update plugin io.freefair.lombok to v8.14.2
* Update plugin io.freefair.maven-publish-java to v8.14.2
* Update plugin net.ltgt.errorprone to v4.3.0
* Update plugin org.springframework.boot to v3.5.4


If you face any issues, please file an [issue at GitHub](https://github.com/kit-data-manager/metastore2/issues). 

