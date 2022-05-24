---
title: Testbed
breadcrumbs: /testbed/
layout: default
description: An example sub-page.
repository_url: https://github.com/kit-data-manager/webpage
repository_name: kit-data-manager/webpage
navigation_id: testbed_index
tag-name: testbed
---

# The # {{ page.title }}

This is an example page used to show how a sub-page stored in a collection may look like. On the top of the page, you 
find meta-information called 'Front Matter' which contains information used by Jekyll or within templates to transport
page-specific properties. The following table lists and explains properties relevant for this project.

| property key    | function                                                                                                                       |sample value
|-----------------|--------------------------------------------------------------------------------------------------------------------------------|----
| title           | The title of the sub-page which will be rendered in the page header.                                                           |example
| breadcrumbs     | The path to this page shown in the breadcrumbs navigation rendered using the template at `_includes/breadcrumbs.html`          |/example/subfolder
| layout          | The layout template used for this page. Layouts are stored in the `_layouts` folder.                                           |default
| description     | A short (catchy) description shown as the page's subtitle.                                                                     |This is an example page
| repository_url  | The URL of the GitHub repository used in templates to provide a link to the most recent version of the presented service/tool. |https://github.com/kit-data-manager/webpage
| repository_name | The name of the repository, i.e., repository_url without protocol and hostname information.                                    |kit-data-manager/webpage
| navigation_id   | The id of the navigation menu taken from `_data\toc.yml`.                                                                      |example_index
| tag-name        | Tag of this page collection, which is used e.g. for assigning news for this sub-page (see below).                              |example
| no_nav          | Boolean property allowing to hide the side navigation for pages which so not have an own navigation entry, e.g., news.         |&lt;any value&gt; 

## News

This page supports the news-feature of Jekyll to allow creating and showing news easily by templating and assign them automatically to the correct sub-page.
Therefor, you may use the template below:

<ul>
  {% for post in site.posts %}
    {% if post.tags contains page.tag-name %}
      <li><a href="/webpage/{{ post.url }}">{{ post.title }}</a>, published {{ post.date | date: "%Y-%m-%d" }}</li>
    {% endif %}
  {% endfor %}
</ul>

This template iterates through all posts of this site located in the `_posts` folder. As there is no way to organize posts in the `_posts` folder directly,
we are using the aforementioned tags to associate a certain sub-page with related posts. In the Front Matter of this page you see the `page-name` property
with the value `example`. This property is used by the snippet above to render only posts which have this tag-name in their list of tags, also specified as
Front Matter property. Please refer to `_posts/example/2022-05-06-example.md` for more information.

## Navigation

The navigation is created within the template (see `_layouts/`) using an included snippet (see `_includes/nav.html`). Its data is written from `_data/toc.yml`
and organized as follows: 

```yml
example_index:
  - title: The top title (can be left empty)
    subfolderitems:
      - title: Sub-Item1
        subfolderitems:
          - page: Sub-Page
            url: example/page1.html
      - title: Sub-Item2
        subfolderitems:
          - page: Sub-Page
            url: example/subfolder/page2.html
          - page: Source Code
            external_url: https://github.com/kit-data-manager/webpage
```

You can see several entries in different hierarchy levels, which are used to generate the navigation tree for the example sub-page. 
It starts with `example_index`, which is the id of the navigation tree used in the Front Matter of the certain sub-page in property `navigation_id`. 
The first title below serves as main caption of the entire navigation and can be omitted, if not needed. Afterwards, you can see the first navigation 
level containing two sub-items. Sub-Item1 contains one additional sub-item referring to a Sub-Page with the relative URL `example/page1.html`. This page is 
generated from a file `_example/page1.md` by Jekyll.
The second sub-item Sub-Item2 contains two more sub-items, the first one referring to another internal page, whereas the other item refers to an external
location, i.e., the source code of this project. In order to be able to use this navigation, it has to be added to `_data/toc.yml`, which is currently not the 
case for this example page.

## Adding the new page to the main index

The main entry point to all sub-pages is the main index file locates at `index.markdown` in the root of this project. In order to add a new item, you have to 
add a new card to this page. Cards are generated using the snippet included from `_includes/card.html` and should look as follows: 

```
{% include card.html tags="example metadata"
target="example/index.html"
background="assets/images/example.jpg"
title="Example"
subtitle="just show how it works"
content="Lorem ipsum dolor sit amet, consectetur adipisicing elit."
%}
```

The template takes some parameters, which are explained in the following table: 

| template parameter | function                                                                                                               |sample value
|--------------------|------------------------------------------------------------------------------------------------------------------------|----
| tags               | Tags which are used to show/hide cards depending on the topic.                                                         |example metadata
| target             | The target page opened if the card's image is clicked.                                                                 |example/index.html
| background         | The upper background image of the card.                                                                                |assets/images/example.jpg
| title              | The card's title.                                                                                                      |Example
| subtitle           | The card's subtitle.                                                                                                   |just show how it works
| content            | The card's text content.                                                                                               |Lorem ipsum dolor sit amet, consectetur adipisicing elit.
