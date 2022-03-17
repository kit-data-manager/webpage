---
title:  "Creating a Data Resource"
layout: default_nav
categories: base-repo general
repository_url: https://github.com/kit-data-manager/base-repo
repository_name: kit-data-manager/base-repo
back: /webpage/base-repo.html
---

#### {{ page.title }}

The following example shows the creation of the first resource only providing mandatory fields:

{% capture my_include %}{% include_relative snippets/create-resource/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

You can see, that most of the sent document is empty. Only title, creator and resourceType are provided by the user. HTTP-wise the call looks as follows: 

{% capture my_include %}{% include_relative snippets/create-resource/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

As Content-Type only 'application/json' is supported and should be provided. The two other headers are typically set by the HTTP client. After validating the 
provided document, adding missing information where possible and persisting the created resource, the result is sent back to the user and will look that way:

{% capture my_include %}{% include_relative snippets/create-resource/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

What you see is, that the result looks different from the original document. A few elements, e.g. identifier, alternateIdentifiers, publisher, publicationYear, dates, acls and state
received a value by the server. Furthermore, you'll find an ETag header with the current ETag of the resource. This value is returned by POST, GET, PUT and PATCH calls and must be provided for 
all calls modifying the resource, e.g. PATCH, PUT and DELETE, in order to avoid conflicts.
