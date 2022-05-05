---
title:  "Introduction"
breadcrumbs: /base-repo/documentation/resource-handling-introduction
layout: default
description: A Generic, General Purpose Research Data Repository Service.
categories: base-repo general
repository_url: https://github.com/kit-data-manager/base-repo
repository_name: kit-data-manager/base-repo
navigation_id: base_repo_doc
---

# {{ page.title }}

In this first section, the handling of data resources on the metadata level is explained. It all starts with creating your first data resource. The resource model of 
KIT Data Manager is based on the DataCite standard. Thus, also the mandatory elements defined by this standard are mandatory at creation time. The following elements
are expected to be provided by the user: 

- Title: At least one title element with arbitrary type (optional) and value must be present.
- ResourceType: The resource type must be assigned by the user. 
- Creators: At least one creator must be present. If no creator is provided by the user, the server will use caller information for adding a creator.
- Dates: One date of type CREATION must be part of every resource. If no such date is provided, the server will use the current date.
- Publisher: The publisher of the resource must be set. If not, the server will use caller information.
- PublicationYear: The publication year should be available. If not, the server will use the current year.

In addition, mentioning how the server handles identifiers might be relevant. There are a couple of identifiers that can be assigned to the resource. The main 
identifier is stored in the field 'identifier'. This field is allowed to hold a single identifier of type 'DOI' in case the resource has a valid DOI or a placeholder.
If the resource has a DOI assigned, this DOI will become the main identifier of the resource. If no 'identifier' is assigned or if the value of 'identifier' represents
a valid placeholder, the list of 'alternateIdentifiers' is checked for an element of type 'INTERNAL'. If one is provided by the user, the value of this element will
be the resource identifier as long as its a unique value. If no alternate identifier of type 'INTERNAL' is available, the server creates one with a UUID as value and uses
this value as resource identifier. Summarizing, this means: 

- If your resource has a DOI, provide the DOI as 'identifier'.
- If your resource has no DOI, but should have a defined identifier, provide the identifier as 'alternateIdentifier' of type 'INTERNAL'.
- If your resource has no DOI and its identifier can be arbitrary, omit any identifier field and leave it to the server to assign an identifier.
