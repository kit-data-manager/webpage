---
title: Introduction
breadcrumbs: /collection-registry/documentation/
layout: default
description: A General Purpose Service for building Research Data Collections.
repository_url: https://github.com/kit-data-manager/collection-api
repository_name: kit-data-manager/collection-api
navigation_id: collection_registry_index
---

# Introduction

A collection is a digital object which bears a unique identifier and binds a finite number of digital objects together, 
which have common concerns. The collection API is an interface specification for CRUD (Create, Read, Update and Delete) 
operations on collections in order to enable client-server interaction with particular observance of persistent identification. 
It can be used for building collections of digital objects independent of any repository in order to facilitate data interoperability, 
reuse and make collections actionable to be able to cope with ever-increasing amounts and volumes of data. The Collection API has been proposed
by the [RDA Recommendation on Research Data Collections](https://zenodo.org/record/2428145#.X0YVOpMzafU). 

The documentation of the different REST APIs is available under [http://rdacollectionswg.github.io/apidocs/#/](http://rdacollectionswg.github.io/apidocs/#/).  
Moreover, this JAVA implementation of the RDA Recommendation is provided as a 
Spring Boot-based Microservice with a complete regard to the recommendation. As some aspects of Collection Registry are not 
clearly defined, the implementation contains some fixes [FIX], additions [ADD] and restrictions [RES]:

* [FIX] Return type inconsistencies have been fixed, e.g. in /collections/{id}/members/{mid}.
* [FIX] Delete operations return status 204 (NO_CONTENT) according to the HTTP specification.
* [FIX] Delete operations are realized idempotent following the HTTP specification. This means, that DELETE can be issued multiple times to a resource and returns HTTP 204 in all cases.
* [FIX] Collection operations allow navigation the same way all other operations do, e.g. via prev and next links.
* [RES] Listing a collection recursively does not consider the sorting of child elements.
* [RES] A recursive listing of a collection will also contain member items of expanded collections.
* [RES] There is currently no build-in PID support. If no PID are provided with a collection or member, a UUID is assigned.
* [ADD] Integrated ETag support in order to avoid concurrent modifications.
* [ADD] Navigation through a result set is realized using default Spring pagination, e.g. supporting page and size query parameters. The cursors (next and prev) of a result set are pointing to the next/prev page link.
