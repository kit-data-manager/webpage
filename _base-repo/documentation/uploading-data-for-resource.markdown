---
title:  "Uploading Data for a Data Resource"
breadcrumbs: /base-repo/documentation/uploading-data-for-resource
layout: default
categories: base-repo general
repository_url: https://github.com/kit-data-manager/base-repo
repository_name: kit-data-manager/base-repo
navigation_id: base_repo_doc
---

### {{ page.title }}

After covering the basics of metadata creation and modification it's time to associate the first file with a created data resource. Uploading data to a KIT Data Manager based repository is also
done using the RESTful API. In order to inform the repository to access data or data-related metadata, you only have to append a path element 'data' to the URL of the actual resource. After this 
'data' path element you are free to organize and name your data as you wish. This allows you to build filesystem-like hierarchies for each data resource. Furthermore, with each file uploaded to
KIT Data Manager a metadata document is connected called 'ContentInformation'. This document contains internal information, e.g. the relative path, the depth in the hierarchy and the parent resource, 
automatically generated metadata, e.g. checksum, size and mime type information, as well as custom information that can be added by the user, e.g. key-value based metadata or tags for grouping content elements.
For the time being, let's stick with the simple case of uploading a single file you can see in the following example.

{% capture my_include %}{% include_relative snippets/upload-file/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

You should pay attention to three different things: first, check the URL. You can see the base URL for the resource we've created before with the aforementioned 'data' element and a filename 'randomFile.txt'. 
This will be the URL where the file is uploaded to and from where it can be downloaded later. The second part worth mentioning is the Content-Type header which is set to 'multipart/form-data'. You always have 
to provide this content type while uploading data, otherwise the upload will fail. Finally, there is the file to upload. For the curl command, it must be provided in the way shown in the example with the -F 
command line option, the argument name 'file' and the reference to the local file, in this example '@randomFile.txt'. How you provide this argument depends on the client or the API you are using.

---
**NOTE**
In the example, the local source file and the destination file name at the server are both 'randomFile.txt'. This is not necessarily required. There can be used an arbitrary name for the file on the server
independent from the original file name.

---

In the HTTP request you can see how the data is submitted. You have your part boundary surrounding the actual content of the file in an encoded form. 

{% capture my_include %}{% include_relative snippets/upload-file/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

Finally, if the file has been uploaded, a response with HTTP status 201 (CREATED) is returned together with the file access URL in the Location header. 

{% capture my_include %}{% include_relative snippets/upload-file/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

Via the file location you can access both: the bitstream of the file as well as metadata collected during file ingest. 
Let's first take a look at the metadata. Therefor, you have to do a simple HTTP GET to the data location telling the server that you request for metadata by adding the Accept header with the value 
'application/vnd.datamanager.content-information+json' as you can see it in the curl command below.

{% capture my_include %}{% include_relative snippets/get-content-metadata/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

The HTTP request holds no surprises, it contains the provided target URL as well as the Accept header for requesting ContentInformation instead of data.

{% capture my_include %}{% include_relative snippets/get-content-metadata/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

With the response you receive on the one hand the current ETag and on the other hand the actual ContentInformation document for the addressed file. All information you can see in the following response
is added by the server during the file ingest.

{% capture my_include %}{% include_relative snippets/get-content-metadata/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

Of course, you can also provide a ContentInformation document during upload, e.g. if you plan to add key-value metadata or tags for a file. In that case you basically do the same as before but you also add 
another file argument with name 'metadata' containing a JSON file with the ContentInformation document.

{% capture my_include %}{% include_relative snippets/upload-file-with-metadata/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

In the HTTP request you now see two content elements: the file 'randomFile2.txt' and the metadata 'metadata.json'. You can choose an arbitrary name for the metadata file, but the content must match the 
ContentInformation model. In the example you see what's in the metadata file. The only element that is relevant is 'metadata' containing a single key 'test' with value 'ok'. There are also other elements
in this file, e.g. depth, size and filename. These are examples for content metadata elements that cannot be set by the user. If there is a value assigned, it will be overwritten during ingest with one 
exception explained later.

{% capture my_include %}{% include_relative snippets/upload-file-with-metadata/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

The response of the upload including content information is identical to the first upload example. If an HTTP status 201 (CREATED) is returned, everything worked out fine and the file as well as the 
ContentInformation document can be accessed via the Location provided in the header.

{% capture my_include %}{% include_relative snippets/upload-file-with-metadata/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

Finally, in some cases, it might not be possible or desired to upload a certain file to the repository, e.g. due to size limitations or due to licensing issues. For these cases it is possible, to just register
a remotely stored file at the local repository. In this scenario, the file argument is omitted during upload and only the ContentInformation metadata document is submitted containing the remote URL in the 
'contentUri' field as you can see it in the following example.

{% capture my_include %}{% include_relative snippets/upload-file-with-reference/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

There is another exception in this special scenario. As there is no guarantee that the file referenced by 'contentUri' is accessible by the repository and for performance reasons, the file is neither checked
nor downloaded at ingest time. Therefore, no size or checksum information will be assigned by the system. If you are aware of these information and if you want to make them available, it is allowed to 
provide the size and checksum element of the ContentInformation document at upload time. They are (only in this case) not overwritten and will be available later, no matter if they are correct or not. 

{% capture my_include %}{% include_relative snippets/upload-file-with-reference/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

Finally, the response of the 'virtual upload' looks as before. However, please keep in mind that there are NO CHECKS of what's behind the contentUri. This happens only at download time, which will be the next 
example. 

{% capture my_include %}{% include_relative snippets/upload-file-with-reference/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}
