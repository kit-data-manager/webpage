---
title:  "Getting a Data Resource"
breadcrumbs: /base-repo/documentation/get-resource
layout: default
description: A Generic, General Purpose Research Data Repository Service.
categories: base-repo general
repository_url: https://github.com/kit-data-manager/base-repo
repository_name: kit-data-manager/base-repo
navigation_id: base_repo_doc
---

# {{ page.title }}

For obtaining accessible data resources you have multiple options: list all resources, access a single resource using a known identifier or search by example. The following example shows how to obtain a 
single resource.

{% capture my_include %}{% include_relative snippets/get-resource/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

In the actual HTTP request there is nothing special. You just access the resource's path using the base path and the resource identifier.

{% capture my_include %}{% include_relative snippets/get-resource/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

As a result, you receive the JSON representation of the resource metadata and again the ETag in the HTTP response header. 

{% capture my_include %}{% include_relative snippets/get-resource/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

Often, it is not enough to access either all resources or only one specific resources, but you want to search for resources following criterias you want to specify. This can be either done using an external service, 
e.g. elasticseach, having all metadata registered or by using the built-in support for finding resources by example. The idea is to allow the user to submit a resource document having values assigned to 
certain fields and to map this resource to a query on the database backend. The main advantage of this approach is its simplicity, the main disadvantage are very basic queries not allowing fine-grained 
selection or other features provided if using a dedicated query language or a search index. That's why for KIT Data Manager both approaches are supported, whereas only the search by example is described in this
document as setting up a search index is quite specific to the use case and will be covered in a separate document.

In order to find resources by example you simple have to POST a resource document all fields filled you want to search for to the endpoint shown in the following curl request: 

{% capture my_include %}{% include_relative snippets/find-resource/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

In our example we search for resources of type DATASET with the type value 'testingSample'. All empty fields in the request can be omitted. You can also see that the endpoint 'dataresources/seach' is based on the
pattern for all other endpoints, so in that case we want to search for data resources. The result of the request will be either an empty response with no element or a list of matching resources. 

{% capture my_include %}{% include_relative snippets/find-resource/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

Also in that case, pagination is supported which you can see in the response header containing the 'Content-Range' key. Internally, assigned values of the example are mapped to queries. Strings are mapped using 'LIKE'
expression with a wildcard character at the beginning and the end. Thus, in our example above also a type value of 'testing' would produce the same result. 

Finding resources by example is supported for data resources as well as for content information. However, there are also some limitations in order to keep it simple and reproducible. The following tables show, which 
attributes are evaluated in which way for creating queries to the data backend.

|Supported Data Resource Fields|Queried as...|Match Type
|----|----|----
|publisher|String|resource.publisher LIKE %value%
|publicationYear|String|resource.publicationYear LIKE %value%
|language|String|resource.language LIKE %value%
|version|String|resource.version LIKE %value%
|state|String|resource.state IN [value]
|resourceType|String|resource.resourceType.typeGeneral=resourceType.typeGeneral AND resource.resourceType.value LIKE %resourceType.value%
|creators|Strings|resource.creator.familyName LIKE %creators.familyName% OR resource.creator.givenName LIKE %creators.givenName% OR resource.creator.affiliation IN [creators.affiliation]
|primaryIdentifier|String|resource.identifier.value IN [primaryIdentifier.value]
|alternateIdentifiers|String|resource.alternateIdentifier.identifierType!=INTERNAL AND resource.alternateIdentifier.value IN [alternateIdentifiers.value]

---
**NOTE**
Other fields will be supported in future. If you require a certain field by your use case. please feel free to file a feature request at GitHub.

---


|Supported Content Information Fields|Queried as...|Match Type 
|----|----|----
|relativePath|String|contentInformation.relativePath LIKE %relativePath%
|contentUri|String|contentInformation.contentUri LIKE %contentUri%
|mediaType|String|contentInformation.mediaType LIKE %mediaType%
|metadata|String|contentInformation.metadata.key=metadata.key AND contentInformation.metadata.value LIKE %metadata.value%
|tags|String|contentInformation.tags IN [tags]


#### Getting a Data Resource by an Alternate Identifier

Typically, the main identifier of the resource, stored in the 'id' field, is used to address a resource. As stated in chapter <<ChapterDataResourceHandling,Data Resource Handling>>
this main identifier is set at resource creation time, either from a provided DOI, a provided identifier of type INTERNAL or by the server. However, you can also use any other identifier to address a resource, 
e.g. the DOI added at a later point or the value of another alternate identifier assigned to the resource. In the following example we are using the alternate identifier of type OTHER we just added 
to the resource via patch operation. The request looks like a typical GET request:

{% capture my_include %}{% include_relative snippets/get-resource-by-alt-id/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

Also the HTTP request shows no difference compared to the GET request shown in the beginning: 

{% capture my_include %}{% include_relative snippets/get-resource-by-alt-id/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

The only difference is how the response looks like. If you are NOT using the main identifier you'll not receive a direct response. Instead, HTTP 303 (SEE_OTHER) is returned together with the link
to the resource including the main identifier in the Location response header. 

{% capture my_include %}{% include_relative snippets/get-resource-by-alt-id/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

However, depending on the utilized HTTP client and its configuration, the redirect might be executed immediately such that you won't be able to spot any difference compared to the direct request 
using the main identifier of the resource.
