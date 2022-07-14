---
title: FAIR DO Cookbook
breadcrumbs: /fairdo-cookbook/
layout: default
description: A collection of recipes for realizing FAIR Digital Objects.
navigation_id: fairdo-cookbook_index
tag-name: fairdo-cookbook
---

# The FAIR DO Cookbook

If you plan to enter the realm of FAIR Digital Objects, the FAIR DO Cookbook could be worth reading. This collection of 
small recipes offers guidance and advice on different aspects related to FAIR DOs. Among others, there are recipes on how
to:

* Create, resolve, and update a PID
* Search for PIDs
* Create a Data Type
* Create a PID Kernel Information Profile
* Validate a PID record against a PID Kernel Information Profile

For some recipes, services from the FAIR Data Commons portfolio are used. If you need more information about a particular
service, please refer to the according sub-page accessible via the [Service Overview](https://kit-data-manager.github.io/webpage/).

To head over directly to the FAIR DO Cookbook, please use the external link in the navigation on the left.


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
