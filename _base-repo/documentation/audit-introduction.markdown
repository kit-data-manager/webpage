---
title:  "Introduction to Audit Features"
breadcrumbs: /base-repo/documentation/audit-introduction
layout: default
categories: base-repo general
repository_url: https://github.com/kit-data-manager/base-repo
repository_name: kit-data-manager/base-repo
navigation_id: base_repo_doc
---

### {{ page.title }}

Not only in living data repositories metadata (and sometimes also data) are subject of change, either by a user or in the course of curation activities. For validation and documentation purposes it can be desirable 
to keep track of these changes, either for monitoring or to be able to rollback unwanted changes at a later point in time. Therefor, KIT Data Manager offers support for capturing audit information and versioning of 
metadata and data. For metadata, it uses the [JaVers](https://javers.org/) library to collect changes between two versions of one document and stores this information in a relational database. With the collected changes
JaVers is capable of creating so called 'Shadows' of a document, which are representing a version at a specific point in time.

For data versioning, there are currently two options build into the base-repo. The first option is not applying data versioning at all. In that case, trying to upload content to a location which already exists is impossible by default but can be enforced, which overwrites previously stored data. The second option is a simple kind of data versioning which appends the current timestamp to each uploaded file. Thus, uploading another version of data to an existing location will result in a new version of the related metadata entity pointing to a new file. Overwriting existing content is not possible while using this kind of versioning.
