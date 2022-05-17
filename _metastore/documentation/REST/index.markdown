---
title: Documentation (REST API)
breadcrumbs: /metastore/documentation/REST
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_doc_rest
---

# {{ page.title }}

In this documentation, the basics of the MetaStore Service are described. You will be guided through the first steps of 
register a JSON schema, read it and update it. After that an appropriate metadata document will be added to MetaStore which is linked to a data resource.

This documentation assumes, that you have an instance of the KIT Data Manager MetaStore repository service installed locally. If the repository is running on another
host or port you should change hostname and/or port accordingly. Furthermore, the examples assume that you are using the repository without authentication
and authorization, which is provided by another service. If you plan to use this optional service, please refer to its documentation first to see how the 
examples in this documentation have to be modified in order to work with authentication. Typically, this should be achieved by simple adding an additional header
entry.

The example structure is identical for all examples below. Each example starts with a CURL command that can be run by copy&paste to your console/terminal window.
The second part shows the response comming from the server.
In between, special characteristics of the calls are explained together with additional, optional arguments or alternative responses.

<style>
td, th {
   border: none!important;
}
</style>
| |[NEXT](introduction-schema.html)|
|:----|----:|
| | |

