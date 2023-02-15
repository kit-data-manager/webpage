---
breadcrumbs: /metastore/news/
layout: default
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
documentation_url: https://kit-data-manager.github.io/
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
no_nav: true
tags: metastore
title:  "MetaStore v1.0.0 released"
---

Today, we like to announce version 1.0.0 of the MetaStore service. Below, you can find the list of changes. 

### Added
- Finalized version of MetaStoreGui
  - Fix issue #69
- Allow also IDs for metadata documents (issue #76)
- Access filter for monitoring.

### Changed
- Update to repo-core 1.0.2
- Update to service-base 1.0.1
- Update to postgresql 42.2.25
- Downgrade library due to some issues regarding validation
  - json-schema-validator 1.0.64. -> 1.0.59 (issue #77)

### Fixed
- Fix bug listing resources without proper authorization (issue #71)
- Fix bug listing all metadata documents related to a specific schema
- Fix a bug that can cause the metadata document/schema to become invalid due to an update. (issue #78)
- Fix bug with path in Windows. (issue #88)
- CSRF is now disabled by default. (issue #70) 
- Check ACLs while creating/updating records (issue #39)
- Added missing spaces to swagger-ui.### Changed
- Truncating service-assigned times to milliseconds for compatibility reasons
- Change of messaging property names including documentation
- Update to service-base 0.2.0
- Update to generic-message-consumer 0.2.0

If you face any issues, please file an [issue at GitHub](https://github.com/kit-data-manager/metastore2/issues). 
