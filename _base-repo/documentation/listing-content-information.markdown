---
title:  "Listing Content Information"
breadcrumbs: /base-repo/documentation/listing-content-information
layout: default
description: A Generic, General Purpose Research Data Repository Service.
categories: base-repo general
repository_url: https://github.com/kit-data-manager/base-repo
repository_name: kit-data-manager/base-repo
navigation_id: base_repo_doc
---

# {{ page.title }}

If you just uploaded the data you still have the data access URL in the Location header of the upload response. However, if you are not the uploader you have to check first, which files are associated with a 
resource in order to obtain a data access URL before download. This can be done by submitting an HTTP GET request to an arbitraty 'virtual folder' as shown in the next example.

{% capture my_include %}{% include_relative snippets/get-content-listing/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

This request will return all content information associated with the addressed resource as we perform a listing of the root data folder. By providing the Accept header with a value 'application/vnd.datamanager.content-information+json'
we ask for ContentInformation metadata as we've learned before. Currently, it is NOT possible to access a 'virtual folder' without providing this header.  

{% capture my_include %}{% include_relative snippets/get-content-listing/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

In the response we get all ContentInformation entries starting with the accessed path. As we provided the root path of the resource's data, we receive all three content elements we've uploaded until now. 

{% capture my_include %}{% include_relative snippets/get-content-listing/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

Listing ContentInformation also support pagination. Furthermore, the results are sorted by their depth within the entire hierarchy of the resource's content. This means, when listing the root folder of a complex content hierarchy, 
you'll first receive all elements directly located at the root folder followed by all elements located in folders of the first hierarchy level and so on.

In addition, you can provide a tag as query argument in order to return only elements having this tag assigned. This allows you to overlay different hierarchies easily and perform a very selective listing of elements.
