---
title:  "Working with Versions"
breadcrumbs: /base-repo/documentation/audit-access
layout: default
description: A Generic, General Purpose Research Data Repository Service.
categories: base-repo general
repository_url: https://github.com/kit-data-manager/base-repo
repository_name: kit-data-manager/base-repo
back: /webpage/base-repo.html
navigation_id: base_repo_doc
---

# {{ page.title }}

Audit and versioning support are seamlessly integrated into the internal workflows and you can benefit from it easily. If you go back to the example of how to <<ChapterGetResource,get a Data Resource>> you'll find in the response
header the property 'Resource-Version' with a value of 1. If you scroll down to the second GET operation performed after updating the resource, you'll see that 'Resource-Version' has been increased to 2. Additionally, a version number
larger than 0 tells you, that versioning is enabled. If not, the version number will be 0, whereas the initial version of a resource is 1.

Now, how can you benefit from this. At first, you might be interested to get all changes applied to a resource. The following request delivers this information. You simply refer to the resource for which you want to obtain audit information
and provide in the 'Accept' header the value 'application/vnd.datamanager.audit+json'.

{% capture my_include %}{% include_relative snippets/get-audit-information/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

As a result you receive a list of changes in a format, which is proprietary to JaVers but which also contains all information in a clear JSON format. Changes are returned ordered by version in decreasing order.

{% capture my_include %}{% include_relative snippets/get-audit-information/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

In the example you can see three changes (starting with the last entry): 

1. The value of property publicationYear has been changed from 2019 (left) to 2017 (right) by the user with id SELF (which is the service itself as we are not using authentication). The result is version 2.
2. The set alternateIdentifiers has been changed by adding the value at index 2. The result is version 3.
3. The value of property publicationYear has been changed back from 2017 to 2019, resulting in the current version 4 of the resource.

Of course, the number of changes can be huge. Therfore, also the listing of audit information supports pagination as explained above for the basic examples. 

Now, what about obtaining a specific version of a resource. This is done as shown in the next request.

{% capture my_include %}{% include_relative snippets/get-resource-version/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

The only thing you have to do is to add a query parameter with name 'version' and the value of the requested version to your GET request. As a result, you'll receive the resource state at the specified version, which is
also stated by the 'Resource-Version' header.

{% capture my_include %}{% include_relative snippets/get-resource-version/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

If you omit the version argument, you always get the most recent version of the resource, in our example it's version 4 as shown below.

{% capture my_include %}{% include_relative snippets/get-current-resource-version/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

As mentioned at the beginning, versioning is supported for metadata resources, e.g. data resources and content information. There is currently no support for versioning of the actual content.
