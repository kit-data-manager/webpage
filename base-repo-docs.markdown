---
layout: default_nav
repository_url: https://github.com/kit-data-manager/base-repo
repository_name: kit-data-manager/base-repo
documentation_url: https://kit-data-manager.github.io/
back: /webpage/base-repo.html
description: A Generic, General Purpose Research Data Repository Service.
---

#### Introduction

In this documentation, the basics of the KIT Data Manager RESTful API of the Repository Service are described. You will be guided through the first steps of creating a data resource, listing existing resources and modifying a single resource on the metadata-level. Furthermore, the same operations on the data level are explained by example.

This documentation assumes, that you have an instance of the KIT Data Manager 2.0 Repository Service installed locally. If the repository is running on another host or port you should change hostname and/or port accordingly. Furthermore, the examples assume that you are using the repository without authentication and authorization, which is provided by another service. If you plan to use this optional service, please refer to its documentation first to see how the examples in this documentation have to be modified in order to work with authentication. Typically, this should be achieved by simple adding an additional header entry.

The example structure is identical for all examples below. Each example starts with a CURL command that can be run by copy&paste to your console/terminal window. The second part shows the HTTP request sent to the server including arguments and required headers. Finally, the third block shows the response comming from the server. In between, special characteristics of the calls are explained together with additional, optional arguments or alternative responses.

---
**NOTE**
For technical reasons, all metadata resources shown in the examples contain all fields, e.g. also empty lists or fields with value 'null'. You may ignore most of them as long as they are not needed. Some of them will be assigned by the server, others remain empty or null as long as you don’t assign any value to them. All fields mandatory at creation time are explained in the resource creation example.

---

 
