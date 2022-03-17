---
title:  "Deleting Data Resources"
layout: default_nav
categories: base-repo general
repository_url: https://github.com/kit-data-manager/base-repo
repository_name: kit-data-manager/base-repo
back: /webpage/base-repo.html
---

#### {{ page.title }}

Finally, after presenting several creation and access scenarios, let's briefly cover the removal of resources. First things first, it is NOT possible to permanently remove resources via the RESTful API. The DELETE operation
is implemented in a way of revoking resources to make them invisible to users, but as they might be references internally or externally, they are never removed from the system unless using additional tools. The following request
shows how a DELETE operation is performed on an existing resource.

{% capture my_include %}{% include_relative snippets/delete-resource/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

You can see that you need the resource URL as well as the current ETag.

{% capture my_include %}{% include_relative snippets/delete-resource/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

The server responds with status HTTP NO_CONTENT (204) to all returning delete requests, even if the resource has been deleted already.

{% capture my_include %}{% include_relative snippets/delete-resource/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

As soon as the resource was REVOKED, no user will be able to see or access the resource. A request to the resource URL will result in an HTTP status NOT_FOUND (404).
However, revoked resources are still visible to the owner(s) of the resource (person(s) possessing ADMINISTATE permission) or the system administrator (person(s) possessing the ADMINISTRATOR role). They still can access
and modify the resource, e.g. in order to change back the state to VOLATILE or FIXED in order to 'undo' the deletion.

If no authentication is enabled, which is assumed by this documentation, the deletion of resources only changes the state to REVOKED. The system account used for authentication-less access is automatically the owner
of all resources, which grants this account the access even to revoked resources. This is shown in the following example.

{% capture my_include %}{% include_relative snippets/get-deleted-resource/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

We are trying a normal HTTP GET to the resource we just deleted. According to the description above, we should receive a positive response showing us a resource with state REVOKED.

{% capture my_include %}{% include_relative snippets/get-deleted-resource/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

The response looks as expected. The resource we've deleted with the changed state. 

{% capture my_include %}{% include_relative snippets/get-deleted-resource/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

That's the reason why another resource state has been introduced in case a resource should be hidden entirely from all users. This state is called GONE and is assigned if a revoked resource is deleted by 
an ADMINISTRATOR. Of course, the GONE state can also be assigned via PATCH operation, but deleting a resource twice is the typical approach to do so. Let's try applying a delete operation a second time.

{% capture my_include %}{% include_relative snippets/delete-resource-twice/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

The response looks as expected delivering status status HTTP NO_CONTENT (204).

{% capture my_include %}{% include_relative snippets/delete-resource-twice/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

However, if we now try to access the resource again via HTTP GET...

{% capture my_include %}{% include_relative snippets/get-gone-resource/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

...we'll receive nothing but the status HTTP NOT_FOUND (404). From now on, the resource is no longer accessible by anybody via RESTful endpoints. The only possibility to re-allow resource access is to modify its state 
in the database.

---
**WARNING**

In contrast to deleting entire resource, deleting single content elements is permanent. If you send a DELETE request to a data URL of a resource, the associated file and all metadata associated with the particular 
element are deleted. This operation is not reversible and you should double check before deleting a content element.

---
