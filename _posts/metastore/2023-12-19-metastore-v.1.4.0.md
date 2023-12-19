---
breadcrumbs: /metastore/news/
layout: default
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
documentation_url: https://kit-data-manager.github.io/
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
no_nav: true
tags: metastore
title:  "MetaStore v1.4.0 released"
---

Today, we like to announce version 1.4.0 of the MetaStore service. Below, you can find the list of changes. 
## Bugfixes
* Filter now combines resourceID AND schemaID instead of OR (#401)

## New Features
* Enable authentication for RabbitMQ (#430)
* Add internal landing page
* Add configuration for redirecting landing page alternatively to external site
* Refine return messages for REST (#399, #402, #403)
* Check usage of schema before deleting (#400)
* Use softlink to jar file in start script
* Metadata schema identifiers support lowercase only
* Endpoints for collections (/api/v1/schemas/, /api/v1/metadata/) are available again. (In addition to /api/v1/schemas and /api/v1/metadata)

## Dependency Upgrades
* Bump com.networknt:json-schema-validator from 1.0.85 to 1.0.86 by @dependabot in [PR 348](https://github.com/kit-data-manager/metastore2/pull/348)
* Bump com.h2database:h2 from 2.1.214 to 2.2.220 by @dependabot in [PR 349](https://github.com/kit-data-manager/metastore2/pull/349)
* Bump gradle from 7.6.1 to 8.2.1. by @VolkerHartmann in [PR 355](https://github.com/kit-data-manager/metastore2/pull/355)
* Bump to gradle from 7.6.1 to 8.2.1 by @github-actions in [PR 354](https://github.com/kit-data-manager/metastore2/pull/354)
* Bump org.springframework.boot from 3.1.0 to 3.1.1 by @github-actions in [PR 358](https://github.com/kit-data-manager/metastore2/pull/358)
* Bump io.spring.dependency-management from 1.1.0 to 1.1.1 by @dependabot in [PR 356](https://github.com/kit-data-manager/metastore2/pull/356)
* Bump io.spring.dependency-management from 1.1.1 to 1.1.2 by @dependabot in [PR 359](https://github.com/kit-data-manager/metastore2/pull/359)
* Bump io.freefair.maven-publish-java from 8.1.0 to 8.2.2 by @dependabot in [PR 364](https://github.com/kit-data-manager/metastore2/pull/364)
* Bump io.spring.dependency-management from 1.1.2 to 1.1.3 by @dependabot in [PR 362](https://github.com/kit-data-manager/metastore2/pull/362)
* Bump com.google.errorprone:error_prone_core from 2.20.0 to 2.21.1 by @dependabot in [PR 361](https://github.com/kit-data-manager/metastore2/pull/361)
* Bump springDocVersion from 2.1.0 to 2.2.0 by @dependabot in [PR 360](https://github.com/kit-data-manager/metastore2/pull/360)
* Bump io.freefair.lombok from 8.1.0 to 8.2.2 by @dependabot in [PR 363](https://github.com/kit-data-manager/metastore2/pull/363)
* Bump docker/setup-buildx-action from 2 to 3 by @dependabot in [PR 374](https://github.com/kit-data-manager/metastore2/pull/374)
* Bump crazy-max/ghaction-docker-meta from 4 to 5 by @dependabot in [PR 371](https://github.com/kit-data-manager/metastore2/pull/371)
* Bump actions/checkout from 3 to 4 by @dependabot in [PR 370](https://github.com/kit-data-manager/metastore2/pull/370)
* Bump docker/setup-qemu-action from 2 to 3 by @dependabot in [PR 373](https://github.com/kit-data-manager/metastore2/pull/373)
* Bump docker/login-action from 2 to 3 by @dependabot in [PR 372](https://github.com/kit-data-manager/metastore2/pull/372)
* Bump org.apache.tika:tika-core from 2.8.0 to 2.9.0 by @dependabot in [PR 369](https://github.com/kit-data-manager/metastore2/pull/369)
* Bump io.freefair.maven-publish-java from 8.2.2 to 8.3 by @dependabot in [PR 368](https://github.com/kit-data-manager/metastore2/pull/368)
* Bump org.mockito:mockito-core from 5.4.0 to 5.5.0 by @dependabot in [PR 366](https://github.com/kit-data-manager/metastore2/pull/366)
* Bump io.freefair.lombok from 8.2.2 to 8.3 by @dependabot in [PR 365](https://github.com/kit-data-manager/metastore2/pull/365)
* Bump org.owasp.dependencycheck from 8.3.1 to 8.4.0 by @dependabot in [PR 367](https://github.com/kit-data-manager/metastore2/pull/367)
* Bump com.networknt:json-schema-validator from 1.0.86 to 1.0.87 by @dependabot in [PR 376](https://github.com/kit-data-manager/metastore2/pull/376)
* Bump com.h2database:h2 from 2.2.220 to 2.2.224 by @dependabot in [PR 375](https://github.com/kit-data-manager/metastore2/pull/375)
* Bump com.google.errorprone:error_prone_core from 2.21.1 to 2.22.0 by @dependabot in [PR 377](https://github.com/kit-data-manager/metastore2/pull/377)
* Bump commons-io:commons-io from 2.13.0 to 2.14.0 by @dependabot in [PR 379](https://github.com/kit-data-manager/metastore2/pull/379)
* Bump docker/build-push-action from 4 to 5 by @dependabot in [PR 378](https://github.com/kit-data-manager/metastore2/pull/378)
* Bump io.freefair.lombok from 8.3 to 8.4 by @dependabot in [PR 380](https://github.com/kit-data-manager/metastore2/pull/380)
* Bump org.mockito:mockito-core from 5.5.0 to 5.6.0 by @dependabot in [PR 381](https://github.com/kit-data-manager/metastore2/pull/381)
* Bump io.freefair.maven-publish-java from 8.3 to 8.4 by @dependabot in [PR 382](https://github.com/kit-data-manager/metastore2/pull/382)
* Bump org.apache.tika:tika-core from 2.9.0 to 2.9.1 by @dependabot in [PR 385](https://github.com/kit-data-manager/metastore2/pull/385)
* Bump org.owasp.dependencycheck from 8.4.0 to 8.4.2 by @dependabot in [PR 384](https://github.com/kit-data-manager/metastore2/pull/384)
* Bump com.google.errorprone:error_prone_core from 2.22.0 to 2.23.0 by @dependabot in [PR 383](https://github.com/kit-data-manager/metastore2/pull/383)
* Bump org.springframework.boot from 3.1.1 to 3.1.5 by @dependabot in [PR 386](https://github.com/kit-data-manager/metastore2/pull/386)
* Bump commons-io:commons-io from 2.14.0 to 2.15.0 by @dependabot in [PR 389](https://github.com/kit-data-manager/metastore2/pull/389)
* Bump org.apache.commons:commons-text from 1.10.0 to 1.11.0 by @dependabot in [PR 390](https://github.com/kit-data-manager/metastore2/pull/390)
* Bump org.mockito:mockito-core from 5.6.0 to 5.7.0 by @dependabot in [PR 391](https://github.com/kit-data-manager/metastore2/pull/391)
* Bump io.spring.dependency-management from 1.1.3 to 1.1.4 by @dependabot in [PR 392](https://github.com/kit-data-manager/metastore2/pull/392)
* Bump org.owasp.dependencycheck from 8.4.2 to 8.4.3 by @dependabot in [PR 394](https://github.com/kit-data-manager/metastore2/pull/394)
* Bump org.owasp.dependencycheck from 8.4.3 to 9.0.1 by @dependabot in [PR 397](https://github.com/kit-data-manager/metastore2/pull/397)
* Bump org.postgresql:postgresql from 42.6.0 to 42.7.0 by @dependabot in [PR 398](https://github.com/kit-data-manager/metastore2/pull/398)
* Bump actions/setup-java from 3 to 4 by @dependabot in [PR 404](https://github.com/kit-data-manager/metastore2/pull/404)
* Bump org.mockito:mockito-core from 5.7.0 to 5.8.0 by @dependabot in [PR 405](https://github.com/kit-data-manager/metastore2/pull/405)
* Bump commons-io:commons-io from 2.15.0 to 2.15.1 by @dependabot in [PR 406](https://github.com/kit-data-manager/metastore2/pull/406)
* Bump springDocVersion from 2.2.0 to 2.3.0 by @dependabot in [PR 407](https://github.com/kit-data-manager/metastore2/pull/407)
* Bump org.owasp.dependencycheck from 9.0.1 to 9.0.2 by @dependabot in [PR 408](https://github.com/kit-data-manager/metastore2/pull/408)
* Bump org.springframework.boot from 3.1.5 to 3.2.0 by @dependabot in [PR 396](https://github.com/kit-data-manager/metastore2/pull/396)
* Bump com.networknt:json-schema-validator from 1.0.87 to 1.0.88 by @dependabot in [PR 423](https://github.com/kit-data-manager/metastoe2/pull/423)
* Bump org.postgresql:postgresql from 42.7.0 to 42.7.1 by @dependabot in [PR 424](https://github.com/kit-data-manager/metastore2/pull/424)
* Bump org.owasp.dependencycheck from 9.0.2 to 9.0.4 by @dependabot in [PR 425](https://github.com/kit-data-manager/metastore2/pull/425)
* Bump javersVersion from 7.0.0 to 7.3.6 by @dependabot in [PR 433](https://github.com/kit-data-manager/metastore2/pull/433)
* Bump org.springframework.data:spring-data-elasticsearch from 5.1.0 to 5.2.0 by @dependabot in [PR 434](https://github.com/kit-data-manager/metastore2/pull/434)
* Bump github/codeql-action from 2 to 3 by @dependabot in [PR 436](https://github.com/kit-data-manager/metastore2/pull/436)
* Bump org.springframework.data:spring-data-elasticsearch from 5.2.0 to 5.2.1 by @dependabot in [PR 437](https://github.com/kit-data-manager/metastore2/pull/437)
* Bump org.owasp.dependencycheck from 9.0.4 to 9.0.7 by @dependabot in [PR 438](https://github.com/kit-data-manager/metastore2/pull/438)
* Bump com.networknt:json-schema-validator from 1.0.88 to 1.1.0 by @dependabot in [PR 439](https://github.com/kit-data-manager/metastore2/pull/439)

If you face any issues, please file an [issue at GitHub](https://github.com/kit-data-manager/metastore2/issues). 
