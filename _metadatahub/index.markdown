---
title: MetadataHub
breadcrumbs: /metadatahub/
layout: default
description: A generic metadata repository for all kind of metadata repositories.
repository_url: https://git.rwth-aachen.de/nfdi4ing/s-3/s-3-3/metadatahub
repository_name: nfdi4ing/s-3/s-3-3/metadatahub
documentation_url: https://kit-data-manager.github.io/
navigation_id: metadatahub_index
tag-name: metadatahub
---

# The MetadataHub

The MetadataHub provides a framework powered by the 'Turntable API'
to access (metadata) repositories with a uniform interface. For this
purpose, developers only need to set up a mapping to the specific 
implementations  they want. This makes it
- easier for developers to provide a User interface independent of the implementaion used.
- easy to provide a low-threshold access to repositories for scientists 
  (once familiar with the user interface, the repository used no longer plays a role).


## Target Audience
- Developers
- Scientists

## Features
* Register/Edit/View schema
* Ingest/Edit/View/Validate metadata documents

<div class="flex flex-wrap -m-3 inset-5px">
        <div class="w-full sm:w-1/2 md:w-1/3 flex-col p-3">
            <h1 class="text-center"><i class="fa-solid fa-circle-question" aria-hidden="true"></i></h1>
            <h3 class="text-center">Further Reading</h3>
            <p>If you want to read more before you give MetadataHub a try, check out the different documents. There you can learn more about the
            <a href="/webpage/metadatahub/documentation/setup.html">setup</a>, or the <a href="/webpage/metadatahub/documentation/installation/index.html">Installation</a>.
            </p>
        </div>
        <div class="w-full sm:w-1/2 md:w-1/3 flex-col p-3">
            <h1 class="text-center"><i class="fa fa-code-fork" aria-hidden="true"></i></h1>
            <h3 class="text-center">Looking for Code?</h3>
            <p>In case you are interested in source-code, check out the <a href="https://git.rwth-aachen.de/nfdi4ing/s-3/s-3-3/metadatahub">GitLab Repository of MetadataHub</a>.
            There you can also open an <a href="https://git.rwth-aachen.de/nfdi4ing/s-3/s-3-3/metadatahub/-/issues">Issue</a> (login required) to report a bug or to 
            request a new feature.</p>
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

