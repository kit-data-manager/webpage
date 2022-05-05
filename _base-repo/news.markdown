---
title: News Archive
breadcrumbs: /base-repo/news/
layout: default
description: A Generic, General Purpose Research Data Repository Service.
repository_url: https://github.com/kit-data-manager/base-repo
repository_name: kit-data-manager/base-repo
documentation_url: https://kit-data-manager.github.io/
navigation_id: base_repo_index
tag-name: base-repo
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
      <div class="fakeimg" style="height:200px;background-image: url('/webpage/assets/images/disks.jpg')"></div>
      <p>{{ post.content }}</p>
    </div>
    {% endif %}
  {% endfor %}
</ul>


