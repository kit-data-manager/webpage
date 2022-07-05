---
title: Turntable API
breadcrumbs: /Turntable API/
layout: default
repository_url: https://git.rwth-aachen.de/nfdi4ing/s-3/s-3-3/turntable-interface
repository_name: s-3/s-3-3/turntable-interface
documentation_url: https://nfdi4ing.pages.rwth-aachen.de/s-3/s-3-3/turntable-interface/
description: A generic API which allows to use multiple repositories.
navigation_id: turntable_index
tag-name: turntable
---

# The Turntable API

The Turntable API defines a uniform interface to metadata repositories. It can serve as a
facade for (multiple) (metadata) repositories. It thus represents the ideal entry point
for developers to
- a unified user interface independent of the repository.
- a service for multiple repostories.

This allows for more effective use of manpower, in addition to simplifying maintenance.

## Target Audience
- Developers

<div class="flex flex-wrap -m-3 inset-5px">
        <div class="w-full sm:w-1/2 md:w-1/3 flex-col p-3">
            <h1 class="text-center"><i class="fa-solid fa-circle-question" aria-hidden="true"></i></h1>
            <h3 class="text-center">Further Reading</h3>
            <p>If you want to read more about turntable API please refer to 
            <a href="https://nfdi4ing.pages.rwth-aachen.de/s-3/s-3-3/turntable-interface/">this</a> external page.
            </p>
        </div>
</div>



## News

<ul>
  {% for post in site.posts %}
    {% if post.tags contains page.tag-name %}
      <li><a href="/webpage/{{ post.url }}">{{ post.title }}</a>, published {{ post.date | date: "%Y-%m-%d" }}</li>
    {% endif %}
  {% endfor %}
</ul>


