---
title:  "Configuration of Audit Features"
breadcrumbs: /base-repo/documentation/audit-configuration
layout: default
categories: base-repo general
repository_url: https://github.com/kit-data-manager/base-repo
repository_name: kit-data-manager/base-repo
back: /webpage/base-repo.html
---

### {{ page.title }}

Enabling or disabling the audit and versioning feature can be done easily by setting the value of the property 'repo.audit.enabled' inside 'application.properties' either 'true' or 'false'. All audit information is stored
in the same database configured for the repository, therefore, no additional configuration is needed. If the feature was not enabled, yet, you can enable it at any time to start capturing audit information beginning with 
the next restart of the repository service. You may also disable the feature again, e.g. temporarily to avoid capturing information, as the primary version of a resource is stored at the repository. 

To enable file versioning, the property 'repo.file.versioning.default' can be either set to 'none' or 'simple'. There is no further configuration necessary.


