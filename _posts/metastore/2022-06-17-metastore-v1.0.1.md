---
breadcrumbs: /metastore/news/
layout: default
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
documentation_url: https://kit-data-manager.github.io/
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
no_nav: true
tags: metastore
title:  "MetaStore v1.0.1 released"
---

Today, we like to announce version 1.0.1 of the metastore service. Below, you can find the list of changes. 

### Security
- Update to h2 2.1.212:
  - Please migrate your database if you want to update MetaStore while using h2!
    See: https://h2database.com/html/migration-to-v2.html 

### Changed
- Update to service-base 1.0.3
- Changed some labels in GUI

### Fixed
- Docker: Add support for M1 chip architecture (issue #107)
- Access public documents of other users is broken.(issue #100)
- Fix bug ignoring type of related resource. (issue #105)
- Fix bug not hiding revoked resources in listings.
- Fix bugs using Swagger UI for REST calls.
- Fix typos in documentation.

If you face any issues, please file an [issue at GitHub](https://github.com/kit-data-manager/metastore2/issues). 
