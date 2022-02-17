---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

#layout: home
---

# Sub-Page

This is a sub-page.

{% for post in site.posts %}
  <h2>{{ post.title }} - {{ post.date }}</h2>
  <p>{{ post.content | markdownify }}</p>
{% endfor %}
