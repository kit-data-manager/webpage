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
    - `metastore.monitoring.cron4schedule`-> removed

### Docker
* Update eclipse-temurin Docker tag to v25

## Dependency Upgrades
* Update actions/checkout action to v6
* Update actions/setup-java action to v5
* Update github/codeql-action action to v4
* Update dependency com.google.errorprone:error_prone_core to v2.42.0
* Update dependency com.google.guava:guava to v33.5.0-jre
* Update dependency com.h2database:h2 to v2.4.240
* Update dependency com.networknt:json-schema-validator to v1.5.9
* Update dependency commons-io:commons-io to v2.21.0
* Update dependency edu.kit.datamanager:repo-core to v1.2.6
* Update dependency edu.kit.datamanager:service-base to v1.3.6
* Update dependency gradle to v9.2.1
* Update dependency io.micronaut.micrometer:micronaut-micrometer-registry-prometheus to v5.13.0
* Update dependency jacoco to v0.8.14
* Update dependency javersVersion to v7.9.0
* Update dependency org.apache.commons:commons-text to v1.14.0
* Update dependency org.apache.tika:tika-core to v3.2.3
* Update dependency org.asciidoctor.jvm.convert to v4.0.5
* Update dependency org.mockito:mockito-core to v5.20.0
* Update dependency org.postgresql:postgresql to v42.7.8
* Update dependency org.springframework.cloud:spring-cloud-gateway-mvc to v4.3.2
* Update dependency org.springframework.boot:spring-boot-starter-actuator to v3.5.8
* Update dependency org.springframework.data:spring-data-elasticsearch to v5.5.6
* Update dependency org.springframework:spring-messaging to v7.0.1
* Update dependency springDocVersion to v2.8.14
* Update plugin com.gorylenko.gradle-git-properties to v2.5.4
* Update plugin io.freefair.lombok to v9.1.0
* Update plugin io.freefair.maven-publish-java to v9.1.0
* Update plugin net.ltgt.errorprone to v4.3.0
* Update plugin org.owasp.dependencycheck to v12.1.9
* Update plugin org.springframework.boot to v3.5.8

If you face any issues, please file an [issue at GitHub](https://github.com/kit-data-manager/metastore2/issues). 

