---
breadcrumbs: /metastore/news/
layout: default
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
documentation_url: https://kit-data-manager.github.io/
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
no_nav: true
tags: metastore
title:  "MetaStore v2.0.1 released"
---

Today, we like to announce version 2.0.1 of the MetaStore service. Below, you can find the list of changes. 

## New Features
 * Remove deleted resource also from search index (if available).
 * ACL entries of resources are now always available. 
 * Add runner for purging deleted resources from database and filesystem.

## Bugfixes
 * Fix error determining correct format of metadata documents
 * Fix problem with transaction while migrating to v2. (remove old ids)

## Dependency Upgrades
 * Update plugin org.springframework.boot to v3.4.1 by @renovate in [PR 621](https://github.com/kit-data-manager/metastore2/pull/621)
 * Update springDocVersion to v2.8.1 by @renovate in [PR 624](https://github.com/kit-data-manager/metastore2/pull/624)
 * Update dependency org.springframework.cloud:spring-cloud-gateway-mvc to v4.2.0 by @renovate in [PR 632](https://github.com/kit-data-manager/metastore2/pull/632)
 * Update dependency org.springframework.cloud:spring-cloud-starter-config to v4.2.0 by @renovate in [PR 633](https://github.com/kit-data-manager/metastore2/pull/633)
 * Update dependency org.springframework.cloud:spring-cloud-starter-netflix-eureka-client to v4.2.0 by @renovate in [PR 634](https://github.com/kit-data-manager/metastore2/pull/634)
 * Update plugin org.owasp.dependencycheck to v11.1.1 by @renovate in [PR 635](https://github.com/kit-data-manager/metastore2/pull/635)
 * Update dependency org.springframework:spring-messaging to v6.2.1 by @renovate in [PR 636](https://github.com/kit-data-manager/metastore2/pull/636)
 * Update dependency org.springframework.data:spring-data-elasticsearch to v5.4.1 by @renovate in [PR 637](https://github.com/kit-data-manager/metastore2/pull/637)
 * Update dependency org.apache.commons:commons-text to v1.13.0 by @renovate in [PR 638](https://github.com/kit-data-manager/metastore2/pull/638)
 * Update dependency com.google.guava:guava to v33.4.0-jre by @renovate in [PR 639](https://github.com/kit-data-manager/metastore2/pull/639)
 * Update plugin io.spring.dependency-management to v1.1.7 by @renovate in [PR 640](https://github.com/kit-data-manager/metastore2/pull/640)
 * Update plugin org.asciidoctor.jvm.convert to v4.0.4 by @renovate in [PR 641](https://github.com/kit-data-manager/metastore2/pull/641)
 * Update dependency gradle to v8.12 by @renovate in [PR 642](https://github.com/kit-data-manager/metastore2/pull/642)
 * Update plugin net.researchgate.release to v3.1.0 by @renovate in [PR 644](https://github.com/kit-data-manager/metastore2/pull/644)
 * Update dependency org.mockito:mockito-core to v5.15.2 by @renovate in [PR 643](https://github.com/kit-data-manager/metastore2/pull/643)
 * Update plugin org.owasp.dependencycheck to v12 by @renovate in [PR 646](https://github.com/kit-data-manager/metastore2/pull/646)
 * Update springDocVersion to v2.8.3 by @renovate in [PR 647](https://github.com/kit-data-manager/metastore2/pull/647)
 * Update dependency org.postgresql:postgresql to v42.7.5 by @renovate in [PR 648](https://github.com/kit-data-manager/metastore2/pull/648)
 * Update dependency com.networknt:json-schema-validator to v1.5.5 by @renovate in [PR 649](https://github.com/kit-data-manager/metastore2/pull/649)
 * Update dependency edu.kit.datamanager:repo-core to v1.2.4 by @renovate in [PR 651](https://github.com/kit-data-manager/metastore2/pull/651)
 * Update dependency edu.kit.datamanager:service-base to v1.3.3 by @renovate in [PR 652](https://github.com/kit-data-manager/metastore2/pull/652)
 * Update dependency org.springframework:spring-messaging to v6.2.2 by @renovate in [PR 650](https://github.com/kit-data-manager/metastore2/pull/650)
 * Update plugin org.owasp.dependencycheck to v12.0.1 by @renovate in [PR 654](https://github.com/kit-data-manager/metastore2/pull/654)
 * Update dependency org.springframework.data:spring-data-elasticsearch to v5.4.2 by @renovate in [PR 653](https://github.com/kit-data-manager/metastore2/pull/653)
 * Update plugin io.freefair.lombok to v8.12 by @renovate in [PR 655](https://github.com/kit-data-manager/metastore2/pull/655)
 * Update plugin org.springframework.boot to v3.4.2 by @renovate in [PR 657](https://github.com/kit-data-manager/metastore2/pull/657)
 * Update dependency gradle to v8.12.1 by @renovate in [PR 658](https://github.com/kit-data-manager/metastore2/pull/658)
 * Update dependency edu.kit.datamanager:repo-core to v1.2.5 by @renovate in [PR 659](https://github.com/kit-data-manager/metastore2/pull/659)
 * Update springDocVersion to v2.8.4 by @renovate in [PR 660](https://github.com/kit-data-manager/metastore2/pull/660)
 * Update plugin org.owasp.dependencycheck to v12.0.2 by @renovate in [PR 661](https://github.com/kit-data-manager/metastore2/pull/661)
 * Update plugin io.freefair.maven-publish-java to v8.12 by @renovate in [PR 656](https://github.com/kit-data-manager/metastore2/pull/656)
 * Update dependency org.apache.tika:tika-core to v3.1.0 by @renovate in [PR 664](https://github.com/kit-data-manager/metastore2/pull/664)
 * Update plugin io.freefair.lombok to v8.12.1 by @renovate in [PR 667](https://github.com/kit-data-manager/metastore2/pull/667)
 * Update plugin io.freefair.maven-publish-java to v8.12.1 by @renovate in [PR 668](https://github.com/kit-data-manager/metastore2/pull/668)

If you face any issues, please file an [issue at GitHub](https://github.com/kit-data-manager/metastore2/issues). 

