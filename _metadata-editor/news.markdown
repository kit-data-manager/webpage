---
title: News Archive
breadcrumbs: /metadata-editor/news/
layout: default
description: A JavaScript library to generate Web Forms for your Metadata.
repository_url: https://github.com/kit-data-manager/metadata-editor
repository_name: kit-data-manager/metadata-editor
navigation_id: metadata_editor_index
tag-name: metadata-editor
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
      <div class="fakeimg" style="height:200px;background-image: url('/webpage/assets/images/editor.png');transform: translate(0px, -100px);"></div>
      <p>{{ post.content }}</p>
    </div>
    {% endif %}
  {% endfor %}
</ul>


