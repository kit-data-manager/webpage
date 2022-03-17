---
title:  "Remarks"
layout: default_nav
categories: base-repo general
repository_url: https://github.com/kit-data-manager/base-repo
repository_name: kit-data-manager/base-repo
back: /webpage/base-repo.html
---

#### {{ page.title }}

While working with versions you should keep some particularities in mind. Access to version is only possible for single resources. There is e.g. no way to obtain all resources in version 2 from the server.
If a specific version of a resource is returned, the obtained ETag also relates to this specific version. Therefore, you should NOT use this ETag for any update operation as the operation will fail with response 
code 412 (PRECONDITION FAILED). Consequently, it is also NOT allowed to modify a format version of a resource. If you want to rollback to a previous version, you should obtain the resource and submit a PUT request
of the entire document which will result in a new version equal to the previous state unless there were changes you are not allowed to apply (anymore), e.g. if permissions have changed. 