---
title: Web Application Protocol Server
breadcrumbs: /wap-server/
layout: default
description: A service for annotating digital content.
navigation_id: wap-server_index
tag-name: wap-server
---

# The Web Application Protocol Server


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
