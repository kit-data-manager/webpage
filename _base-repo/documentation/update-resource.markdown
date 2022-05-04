---
title:  "Updating a Data Resource"
breadcrumbs: /base-repo/documentation/update-resource
layout: default
categories: base-repo general
repository_url: https://github.com/kit-data-manager/base-repo
repository_name: kit-data-manager/base-repo
navigation_id: base_repo_doc
---

### {{ page.title }}

The default way of updating resources' metadata in KIT Data Manager is by using HTTP PATCH. Therefor, JSON Patch documents following the RFC 6902 specification are sent to the server stating 
which operation should be applied to which field with which value. A sample request is shown below.

{% capture my_include %}{% include_relative snippets/patch-resource/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

In this simple example we change the publicationYear property of a resource. Therefor, we are using the operation 'replace', the path '/publicationYear' and the new value "2017". 
Thus, you need to know a few things in order to create a patch document:

1. Which operation should be used? - Please refer to the RFC 6902 specification for available operations.
2. Which path should be affected? - The path is defined by the model of KIT Data Manager's data resources. If you want to modify an array you should know that the index starts with 0 and you should also know
the number of elements before the patch operation in order to add the new element to index current + 1.
3. Which kind of value must be provided? - Depending on the provided path you'll either have to provide a primitive value, e.g. a string like "new value" or a number like 123, or you have to provide a JSON object.

As soon as you have created your patch document, you can send it to the server using the HTTP verb PATCH and the ETag of the resource. Furthermore, you have to provide the Content-Type 'application/json-patch+json'
in order to state that you're sending a patch document. A valid request will then look as follows:

{% capture my_include %}{% include_relative snippets/patch-resource/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

If a patch could be applied, you'll receive a response with HTTP status 204 (NO_CONTENT). If this is the case, you can assume that the resource has been changed. If the patch document was invalid, HTTP 400 (BAD_REQUEST)
will be returned.

{% capture my_include %}{% include_relative snippets/patch-resource/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

---
**NOTE**
If you want to apply multiple patch operations you do not have to send one request per operation. Instead you can submit an array of patch operations within one single request. In case of a positive response of HTTP 204, 
all patch operations have been applied.

---

If you now request the patched resource you will see all modifications included: 

{% capture my_include %}{% include_relative snippets/get-patched-resource/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

{% capture my_include %}{% include_relative snippets/get-patched-resource/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

In the next example, a more complex patch operation is shown adding a new alternate identifier. We are using the patch operation 'add' affecting the path '/alternateIdentifiers/1' with a value containing a
JSON object representing the new identifier. Using the index 1 is because each resource has by default one alternate identifier of type INTERNAL assigned accessible at index 0. However, it's more save to 
check the resource first before trying to add a new element to an array in order to provide the correct index. Otherwise, if you try to add an element to an existing index, HTTP 400 (BAD_REQUEST) will be returned. 
The request for adding a new alternate identifier should look as follows:

{% capture my_include %}{% include_relative snippets/patch-resource-complex/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

Bear also in mind, that the value of the patch operation contains a value matching the addressed path in the same format as it would be returned by the server. Thus, you don't need any escaping of
array elements or numbers. Only strings have to be quoted. The HTTP request including the proper Content-Type and mandatory ETag is shown in the block below followed by the response we already know.

{% capture my_include %}{% include_relative snippets/patch-resource-complex/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

{% capture my_include %}{% include_relative snippets/patch-resource-complex/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

If you now obtain the patched resource you'll see that there are two alternate identifiers, the INTERNAL one and the identifier of type OTHER we just added.

{% capture my_include %}{% include_relative snippets/get-patched-resource-complex/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

{% capture my_include %}{% include_relative snippets/get-patched-resource-complex/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

Besides the possiblity of patching resources there is also the option to apply updates to an existing resource via HTTP PUT. This rather traditional approach requires the user to read a resource,
apply updates locally and send the modified resource back to the server. This approach may seem more intuitive but can also causes a comparibly huge overhead as also unchanged content is sent between
client and server. To illustrate the impact, let's go back to the update example in the beginning. In order to update the publication year the following requests are necessary:

1. HTTP HEAD /api/v1/dataresources/f1062088-3946-410c-8d85-b64f3d6f0751 in order to obtain the current ETag w/o requesting the entire resource (not shown in the example)
2. HTTP PATCH /api/v1/dataresources/f1062088-3946-410c-8d85-b64f3d6f0751 sending 77 bytes of patch document
3. HTTP GET /api/v1/dataresources/f1062088-3946-410c-8d85-b64f3d6f0751 requesting 1202 bytes to read the resource after patching it (not necessary, just for a fair comparison)

Summarizing, approx. 1300 bytes of payload were transferred. If we now take a look at the same operation using HTTP PUT it looks as follows:

1. HTTP GET /api/v1/dataresources/f1062088-3946-410c-8d85-b64f3d6f0751 requesting 1202 bytes to read the resource itself as we have to apply changes client-side and the current ETag and the
2. Apply changes locally, e.g. set the new publication year
3. HTTP PUT /api/v1/dataresources/f1062088-3946-410c-8d85-b64f3d6f0751 sending 1202 bytes of data containing the changed resource and receiving 1202 bytes of data (the modified resource) as response

You can see that in the second scenario the entire resource is sent three times summing up to around 3600 bytes of data. For a single requests this doesn't seem to be much, but just imagine the overhead
produced by hundreds or thousands of users working actively with the system. Then a factor of three definitely matters.

However, let's wrap this up with the example of the PUT operation being aware that it should only be used if there are good reasons to do so.

{% capture my_include %}{% include_relative snippets/put-resource/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

As described before, the entire document is send with the PUT request including the current ETag of the resource.

{% capture my_include %}{% include_relative snippets/put-resource/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

Finally, the updated resource is sent back to the user in the response body together with HTTP status 200 (OK) if the update was successful.

{% capture my_include %}{% include_relative snippets/put-resource/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

#### Rules for Applying Updates

Before you try to update a certain resource and wonder why the update fails for unknown reasons, please check the following rules for updating resources as not all fields can be updated (by everybody). 
These rules apply to both scenarios, updating via PATCH and PUT.

- It is NOT allowed to update any field named 'id'. This is for technical reasons as these ids are used internally for indexing and linking, therefore changes would influence the integrity of the system.
- Performing updates requires WRITE permissions to the updated resource. This only applies if authorization is enabled, which is not part of this document. Without active authorization, each request is executed with WRITE permissions.
- With WRITE permissions, Resources can only be updated as long as their state is VOLATILE. If the state is changed to FIXED, only the owner and administrators are allowed to update the resource. This only applies if authorization is enabled, 
which is not part of this document. Without active authorization, the state has no influence.
- The array 'acls' can only be changed by the owner or an administrator. This only applies if authorization is enabled, which is not part of this document. Without active authorization, acls have no influence.
- Each value of 'identifier' and 'alternateIdentifiers' of all resources must be unique. This is due to the fact, that a resource can be accessed by all its identifiers and allowing duplicated identifiers would cause equivocal results.

If one of these rules is violated, an according HTTP status code is returned, e.g. BAD_REQUEST, FORBIDDEN or CONFLICT. 
