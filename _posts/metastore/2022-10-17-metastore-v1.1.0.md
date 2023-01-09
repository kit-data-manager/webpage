---
breadcrumbs: /metastore/news/
layout: default
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
documentation_url: https://kit-data-manager.github.io/
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
no_nav: true
tags: metastore
title:  "MetaStore v1.1.0 released"
---

Today, we like to announce version 1.1.0 of the metastore service. Below, you can find the list of changes. 

### Security
- Switch to 'eclipse-temurin' for docker due to end of support for 'openjdk'.

### Added
- More specific messages for creating/updating metadata documents.
- Add ACL info for services to enable authorization.
- Support for Keycloak tokens.

### Changed
- Update to service-base 1.0.7
- Update to repo-core 1.0.4
- Update to javers 6.6.5
- Update to io.freefair.lombok 6.5.1
- Update to org.owasp.dependencycheck 7.2.1
- Update to spring-boot 2.7.4
- Update to spring-doc 1.6.11
- Update to spring-cloud 3.1.4
- Update to spring-messaging 5.3.23
- Update to postgresql 42.5.0
- Update to h2 2.1.214
- Update to gradle version 7.5.1
- Remove powermock
- Support for Java 17 (tests)
- Remove jwt libraries (already part of service-base).

If you face any issues, please file an [issue at GitHub](https://github.com/kit-data-manager/metastore2/issues). 
