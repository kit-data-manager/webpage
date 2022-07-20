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

To head over directly to the FAIR DO Cookbook, please use the external link in the navigation on the left. Otherwise, you may want to start with one of the topics below.


<div class="flex flex-wrap -m-3 inset-5px">
        <div class="w-full sm:w-1/2 md:w-1/3 flex-col p-3">
            <h1 class="text-center"><i class="fa-solid fa-circle-info" aria-hidden="true"></i></h1>
            <h3 class="text-center">More Information</h3>
            <p>For some recipes, services from the FAIR Data Commons portfolio are used. If you need more information about a particular
service, please refer to the according sub-page accessible via the <a href="https://kit-data-manager.github.io/webpage/">Service Overview</a>.
            </p>
        </div>
        <div class="w-full sm:w-1/2 md:w-1/3 flex-col p-3">
            <h1 class="text-center"><i class="fa-solid fa-file-circle-plus" aria-hidden="true"></i></h1>
            <h3 class="text-center">Request for Recipe</h3>
            <p>If you miss a certain recipe and you want to share your idea, please create a 
            <a href="https://github.com/kit-data-manager/webpage/issues/new?assignees=&labels=recipe&template=recipe-request.md&title=%5BRECIPE%5D+Your+recipe+title
">New Recipe Issue</a> and we'll get in touch with you.
            </p>
        </div>
        <div class="w-full sm:w-1/2 md:w-1/3 flex-col p-3">
            <h1 class="text-center"><i class="fa fa-code-fork" aria-hidden="true"></i></h1>
            <h3 class="text-center">Looking for Code?</h3>
            <p>In case you are interested in source-code, check out the <a href="https://github.com/kit-data-manager/fairdo-cookbook/tree/gh-pages">GitHub Repository of the FAIR DO Cookbook</a>.</p>
        </div>
</div>



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
