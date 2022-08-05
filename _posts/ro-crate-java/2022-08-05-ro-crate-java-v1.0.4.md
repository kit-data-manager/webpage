---
breadcrumbs: /ro-crate-java/news/
layout: default
repository_url: https://github.com/kit-data-manager/ro-crate-java
repository_name: kit-data-manager/ro-crate-java
description: A library to create and modify valid RO-Crates.
no_nav: true
tags: ro-crate-java
title:  "ro-crate-java v1.0.4 released"
date: 2022-08-05
---

# ro-crate-java v1.0.4 released

Today, we like to announce the release of version 1.0.4 of ro-crate-java.

## Highlights

Changes at [ror.org](https://ror.org) required a small adjustment on ro-crate-java for cases where the identifier does not exist. Cases where the identifier was correct were not affected.

The adjustment affected the mapping from ROR metadata to RO-Crate contextual entities. It allows creating an organization entity for RO-Crates from the ROR metadata, using a single line of code. You can then add it to the crate and associate it with other entities within this crate. The following line works in every version:

```java
OrganizationEntity organizationEntity = RorProvider.getOrganization("https://ror.org/04t3en479");
```

But a line like this would crash in previous versions, because of changes at ROR:

```java
OrganizationEntity organizationEntity = RorProvider.getOrganization("https://ror.org/not-a-real-id");
```

## Other changes

All other changes are about maintenance: all libraries have been updated to their newest versions. For technical details and maintenance information of this release, please take a look at the [release page](https://github.com/kit-data-manager/ro-crate-java/releases/tag/v1.0.4).