---
title: News Archive (Turntable API)
breadcrumbs: /turntable/news/
layout: default
repository_url: https://git.rwth-aachen.de/nfdi4ing/s-3/s-3-3/turntable-interface
repository_name: s-3/s-3-3/turntable-interface
documentation_url: https://nfdi4ing.pages.rwth-aachen.de/s-3/s-3-3/turntable-interface/
description: A generic API which allows to use multiple repositories.
navigation_id: turntable_index
tag-name: turntable
---

# News Archive (MetaStore)

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


