---
title: News Archive
breadcrumbs: /wap-server/news/
layout: default
repository_url: https://github.com/kit-data-manager/wap-server
repository_name: kit-data-manager/wap-server
description: A service for annotating digital content.
navigation_id: wap-server_index
tag-name: wap-server
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
      <div class="fakeimg" style="height:200px;background-image: url('/webpage/assets/images/annotation.jpg')"></div>
      <p>{{ post.content }}</p>
    </div>
    {% endif %}
  {% endfor %}
</ul>


