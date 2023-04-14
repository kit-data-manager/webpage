---
breadcrumbs: /metastore/news/
layout: default
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
documentation_url: https://kit-data-manager.github.io/
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
no_nav: true
tags: metastore
title:  "MetaStore v1.2.3 released"
---

Today, we like to announce version 1.2.3 of the MetaStore service. Below, you can find the list of changes. 

## New Features
* Add CITATION.cff by @github-actions in [Issue 235](https://github.com/kit-data-manager/metastore2/issues/235)
* Allow cli arguments for start script
* Enable configuration to organize internal storage of metadata documents [Issue 236](https://github.com/kit-data-manager/metastore2/issues/241)

## Bugfixes
* Setting the version number when updating a schema overwrites the original document. by @github-actions in [Issue 245](https://github.com/kit-data-manager/metastore2/issues/245)
* Trace log may slow down service. [Issue 233](https://github.com/kit-data-manager/metastore2/issues/233)
* Calling REST-Endpoint for UI fails if no page information is provided. [Issue 264](https://github.com/kit-data-manager/metastore2/issues/264)
* Problem running MetaStore standalone in a docker container. [Issue 270](https://github.com/kit-data-manager/metastore2/issues/270)

## Dependency Upgrades
* Bump com.networknt:json-schema-validator from 1.0.77 to 1.0.78 by @dependabot in [PR 240](https://github.com/kit-data-manager/metastore2/pull/240)
* Bump org.springframework.cloud:spring-cloud-starter-config from 3.1.5 to 3.1.6 by @dependabot in [PR 239](https://github.com/kit-data-manager/metastore2/pull/239)
* Bump org.springframework.data:spring-data-elasticsearch from 4.4.8 to 4.4.9 by @dependabot in [PR 238](https://github.com/kit-data-manager/metastore2/pull/238)
* Bump org.owasp.dependencycheck from 8.1.0 to 8.1.2 by @dependabot in [PR 237](https://github.com/kit-data-manager/metastore2/pull/237)
* Bump org.mockito:mockito-core from 5.1.1 to 5.2.0 by @dependabot in [PR 244](https://github.com/kit-data-manager/metastore2/pull/244)
* Bump springDocVersion from 1.6.14 to 1.6.15 by @dependabot in [PR 243](https://github.com/kit-data-manager/metastore2/pull/243)
* Bump edu.kit.datamanager:repo-core from 1.1.1 to 1.1.2 by @dependabot in [PR 252](https://github.com/kit-data-manager/metastore2/pull/252)
* Bump org.springframework:spring-messaging from 5.3.25 to 5.3.26 by @dependabot in [PR 251](https://github.com/kit-data-manager/metastore2/pull/251)
* Bump org.postgresql:postgresql from 42.5.4 to 42.6.0 by @dependabot in [PR 250](https://github.com/kit-data-manager/metastore2/pull/250)
* Bump javersVersion from 6.11.0 to 6.12.0 by @dependabot in [PR 249](https://github.com/kit-data-manager/metastore2/pull/249)
* Bump edu.kit.datamanager:service-base from 1.1.0 to 1.1.1 by @dependabot in [PR 248](https://github.com/kit-data-manager/metastore2/pull/248)
* Bump org.springframework.boot from 2.7.9 to 2.7.10 by @dependabot in [PR 259](https://github.com/kit-data-manager/metastore2/pull/259)
* Bump org.owasp.dependencycheck from 8.1.2 to 8.2.1 by @dependabot in [PR 260](https://github.com/kit-data-manager/metastore2/pull/260)
* Bump javersVersion from 6.12.0 to 6.13.0 by @dependabot in [PR 262](https://github.com/kit-data-manager/metastore2/pull/262)
* Bump io.freefair.lombok from 6.6.3 to 8.0.1 by @dependabot in [PR 263](https://github.com/kit-data-manager/metastore2/pull/263)
* Bump io.freefair.maven-publish-java from 6.6.3 to 8.0.1 by @dependabot in [PR 261](https://github.com/kit-data-manager/metastore2/pull/261)
* Bump org.springframework.data:spring-data-elasticsearch from 4.4.9 to 4.4.10 by @dependabot in [PR 269](https://github.com/kit-data-manager/metastore2/pull/269)
* Bump com.networknt:json-schema-validator from 1.0.78 to 1.0.79 by @dependabot in [PR 268](https://github.com/kit-data-manager/metastore2/pull/268)
* Bump javersVersion from 6.13.0 to 6.14.0 by @dependabot in [PR 267](https://github.com/kit-data-manager/metastore2/pull/267)
* Bump springDocVersion from 1.6.15 to 1.7.0 by @dependabot in [PR 266](https://github.com/kit-data-manager/metastore2/pull/266)
* Bump to gradle from 7.6 to 7.6.1 by @github-actions in [PR 266](https://github.com/kit-data-manager/metastore2/pull/273)
* Bump org.mockito:mockito-core from 5.2.0 to 5.3.0 by @dependabot in [PR 276](https://github.com/kit-data-manager/metastore2/pull/276)

If you face any issues, please file an [issue at GitHub](https://github.com/kit-data-manager/metastore2/issues). 
