---
title: Setup MetadataHub
breadcrumbs: /metadatahub/documentation/Setup
layout: default
description: A generic metadata repository for all kind of metadata repositories.
repository_url: https://git.rwth-aachen.de/nfdi4ing/s-3/s-3-3/metadatahub
repository_name: nfdi4ing/s-3/s-3-3/metadatahub
documentation_url: https://kit-data-manager.github.io/
navigation_id: metadatahub_index
---

# {{ page.title }} 

The service contains a subdirectory called 'mappings' which contains all
mappings to linked repositories. 
## The 'mappings' directory
All mappings have to fulfill the following conditions:
- JSON format
- valid against [this schema](https://git.rwth-aachen.de/nfdi4ing/s-3/s-3-3/metadatahub/-/blob/main/src/main/resources/json/schema/http_mapping.json).
- filename ends with '*_mappings.json'

For examples take a look [here](https://git.rwth-aachen.de/nfdi4ing/s-3/s-3-3/metadatahub/-/blob/main/mappings/applicationProfile_mappings.json)

'clientId' has to be unique!

Variables can be referenced via there name.
e.g.: 
{example} can be used as replacement for the specific value of 'example'.

If the variable must be URL encoded it can be referenced via 
'{url_encode(example)}'.

If only parts of a variable should be used this is possible using the grouping syntax of regexp. 

**For example:**

Prefix of a variable: 

example=prefix/value --> {example(^(.*)/.*)}

