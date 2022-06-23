---
title: RO-Crate-Java
breadcrumbs: /ro-crate-java/
layout: default
description: A library to create and modify valid RO-Crates.
repository_url: https://github.com/kit-data-manager/ro-crate-java
repository_name: kit-data-manager/ro-crate-java
navigation_id: ro-crate-java_index
tag-name: ro-crate-java
---

# The {{ page.title }} library

[Research-Object-Crate](https://www.researchobject.org/) is a flexible research data package format. It allows you to package or link to data and describe it in a machine-readable and human-readable way. It uses Linked Data (JSON-LD) to describe its content. The combination of a file-based package and a possibility to link to data on the Web makes the format useful for a number of use-cases.

Software libraries enable developers and users to create and modify such crates. They have the potential to enable valid crates without knowing the specification perfectly, and can be used to build this functionality into other applications.

Ro-crate-java is such a software library, written in the Java programming language. It has similar functionality as the existing implementations (ro-crate-py, ro-crate-ruby), which are implemented by the RO-Crate project. In contrast to those implementations, ro-crate-java has a strong focus on the correctness of the crates according to the specification, as well as performance. This means that ro-crate-java is especially well suited to create large crates, or large amounts of them. It can therefore, for example, be used to create crates for data in large repositories which are not packaged yet.

In the context of development, we created benchmarks to compare the existing implementations. This allows developers of all implementations to find its weaknesses and strengths, but on the other hand also enables users to decide which implementation to use.


## Features

- Create and modify RO-Crates using a convenient API (extensive use of the Builder pattern)
- Support of the limitless possibilities of Linked Data to describe your data
- Performant implementation for large (amounts of) tasks
- Benchmarks comparing the different implementations


## Roadmap

Ro-crate-java has been extensively tested using unit and integration tests and was successfully used in tests with existing crates, as well as examples from the specification. Yet, it is currently not being integrated in other software and has not experienced large amounts of use in practice, which is why we consider it beta software. We encourage you to try it for your project, to change this situation. Of course, we have a certain roadmap to do so ourself.

- Apply the library in our own repositories and tools.

  We are planning to integrate it with our software and use it in real projects.


{% assign servicePosts = site.posts | where_exp: "post", "post.tags contains page.tag-name" %}
{% assign amountPosts = servicePosts | size %}
{% if amountPosts > 0 %}
## News

<ul>
  {% for post in servicePosts %}
      <li><a href="/webpage/{{ post.url }}">{{ post.title }}</a>, published {{ post.date | date: "%Y-%m-%d" }}</li>
  {% endfor %}
</ul>
{% endif %}
