---
title: News Archive (MetadataHub)
breadcrumbs: /metadatahub/news/
layout: default
description: A generic metadata repository for all kind of metadata repositories.
repository_url: https://git.rwth-aachen.de/nfdi4ing/s-3/s-3-3/metadatahub
repository_name: nfdi4ing/s-3/s-3-3/metadatahub
documentation_url: https://kit-data-manager.github.io/
navigation_id: metadatahub_index
tag-name: metadatahub
---

# News Archive (MetadataHub)

<ul>
  {% for post in site.posts %}
    {% if post.tags contains page.tag-name %}
      <!-- li><a href="/webpage/{{ post.url }}">{{ post.title }}</a>, published {{ post.date | date: "%Y-%m-%d" }}</li-->
      <!-- p>{{ post.content }}</p-->
    <div class="news_card">
      <h2>{{ post.title }}</h2>
      <h5>published {{ post.date | date: "%Y-%m-%d" }}</h5>
      <div class="fakeimg" style="height:200px;background-image: url('/webpage/assets/images/turntable.png')"></div>
      <p>{{ post.content }}</p>
    </div>
    {% endif %}
  {% endfor %}
</ul>


