---
title: News Archive
breadcrumbs: /collection-registry/news/
layout: default
repository_url: https://github.com/kit-data-manager/collection-api
repository_name: kit-data-manager/collection-api
description: A General Purpose Service for building Research Data Collections.
navigation_id: collection_registry_index
tag-name: collection-registry
---

# News Archive

<ul>
  {% for post in site.posts %}
    {% if post.tags contains page.tag-name %}
      <!-- li><a href="/webpage/{{ post.url }}">{{ post.title }}</a>, published {{ post.date | date: "%Y-%m-%d" }}</li-->
      <!-- p>{{ post.content }}</p-->
    <div class="news_card">
      <h2>{{ post.title }}</h2>
      <h5>published {{ post.date | date: "%Y-%m-%d" }}</h5>
      <div class="fakeimg" style="height:200px;background-image: url('/webpage/assets/images/collections.jpg')"></div>
      <p>{{ post.content }}</p>
    </div>
    {% endif %}
  {% endfor %}
</ul>


