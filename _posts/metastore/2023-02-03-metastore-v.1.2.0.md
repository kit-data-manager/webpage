---
breadcrumbs: /metastore/news/
layout: default
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
documentation_url: https://kit-data-manager.github.io/
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
no_nav: true
tags: metastore
title:  "MetaStore v1.2.0 released"
---

Today, we like to announce version 1.2.0 of the metastore service. Below, you can find the list of changes. 

## New Features
* Add proxy for authenticated search via elasticsearch
* Add commandline parser for reindexing elasticsearch
* Add actuator endpoints for info and health (https://github.com/kit-data-manager/metastore2/issues/184)
 
## Bugfixes
* Invalid input for resource identifier causes NPE (https://github.com/kit-data-manager/metastore2/issues/198)
* Hibernate validation was not enabled by default. (https://github.com/kit-data-manager/metastore2/issues/191)
* Check metadata directory for valid entry during startup (https://github.com/kit-data-manager/metastore2/issues/185)

## Dependency Upgrades
* Bump commons-text from 1.9 to 1.10.0
* Bump gradle from 7.5.1 to 7.6. by @VolkerHartmann in https://github.com/kit-data-manager/metastore2/pull/172
* Bump httpclient from 4.5.13 to 4.5.14 by @dependabot in https://github.com/kit-data-manager/metastore2/pull/145
* Bump io.freefair.lombok from 6.6 to 6.6.1 by @dependabot in https://github.com/kit-data-manager/metastore2/pull/150
* Bump io.freefair.lombok from 6.5.1 to 6.6 by @dependabot in https://github.com/kit-data-manager/metastore2/pull/138
* Bump io.freefair.maven-publish-java from 6.5.1 to 6.6.1 by @dependabot in https://github.com/kit-data-manager/metastore2/pull/155
* Bump io.spring.dependency-management from 1.0.14.RELEASE to 1.1.0 
* Bump javersVersion from 6.6.5 to 6.8.2 by @dependabot in https://github.com/kit-data-manager/metastore2/pull/164
* Bump json-schema-validator from 1.0.73 to 1.0.76 by @dependabot in https://github.com/kit-data-manager/metastore2/pull/154
* Bump mockito-core from 4.8.1 to 5.1.0 by @dependabot in https://github.com/kit-data-manager/metastore2/pull/194
* Bump org.owasp.dependencycheck from 7.3.0 to 8.0.2 by @dependabot in https://github.com/kit-data-manager/metastore2/pull/176
* Bump org.springframework.boot from 2.7.6 to 2.7.8 by @dependabot in https://github.com/kit-data-manager/metastore2/pull/188
* Bump postgresql from 42.5.0 to 42.5.1
* Bump repo-core from 1.0.4 to 1.1.1 by @dependabot in https://github.com/kit-data-manager/metastore2/pull/195
* Bump service-base from 1.0.7 to 1.1.0. by @VolkerHartmann in https://github.com/kit-data-manager/metastore2/pull/175
* Bump SpringBoot from 2.7.4 to 2.7.6 by @VolkerHartmann in https://github.com/kit-data-manager/metastore2/pull/143
* Bump springDocVersion from 1.6.11 to 1.6.14 by @dependabot in https://github.com/kit-data-manager/metastore2/pull/166
* Bump spring-cloud-starter-config from 3.1.4 to 3.1.5
* Bump spring-cloud-gateway-mvc from 3.1.4 to 3.1.5 by @dependabot in https://github.com/kit-data-manager/metastore2/pull/197
* Bump spring-data-elasticsearch from 4.4.6 to 4.4.7 by @dependabot in https://github.com/kit-data-manager/metastore2/pull/193
* Bump spring-messaging from 5.3.23 to 5.3.25 by @dependabot in https://github.com/kit-data-manager/metastore2/pull/163
* Bump spring-restdocs-mockmvc:from 2.0.6.RELEASE to 2.0.7.RELEASE
* Bump spring-security-config from 5.5.2 to 5.7.5
* Bump spring-security-web from 5.7.2 to 5.7.5
* Bump tika-core from 1.2.7 to 2.6.0 
* Bump xercesImpl from 2.12.1 to 2.12.2 

If you face any issues, please file an [issue at GitHub](https://github.com/kit-data-manager/metastore2/issues). 
