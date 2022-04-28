---
title:  "Downloading Data from a Data Resource"
breadcrumbs: /base-repo/documentation/downloading-data-from-resource
layout: default
categories: base-repo general
repository_url: https://github.com/kit-data-manager/base-repo
repository_name: kit-data-manager/base-repo
---

### {{ page.title }}

After explaining how metadata and data are put into the system, let's give a brief overview on downloading content. Actually, it's just putting the file URL received during upload to the browser address bar or 
to issue a GET request without Accept header as you can see in the curl command below.

{% capture my_include %}{% include_relative snippets/download-file/curl-request.md %}{% endcapture %}
{{ my_include | markdownify }}

There is not much to say about the HTTP request as it only contains the location of the data...

{% capture my_include %}{% include_relative snippets/download-file/http-request.md %}{% endcapture %}
{{ my_include | markdownify }}

...and the response contains the content of the file. That's all in case the file is located at the repository.

{% capture my_include %}{% include_relative snippets/download-file/http-response.md %}{% endcapture %}
{{ my_include | markdownify }}

If the content is not located at the repository but referenced from remote, there are plenty of possible responses depending on the availability of the referenced content. While accessing references content,
the repository tries to issue an HTTP GET to the content URI. Depending on the response status received from the remote service, the repository responds as follows:

|Response from Remote Service|Response by Repository
|---|---
|None|SERVICE_UNAVAILABLE (503)
|OK (200)|SEE_OTHER (303) with Content URI in 'Location' header
|MOVED_PERMANENTLY (301), FOUND (302), SEE_OTHER (303),TEMPORARY_REDIRECT (307), PERMANENT_REDIRECT (308) with 'Location' header|Previous response status with Content URI in 'Location' header
|MOVED_PERMANENTLY (301), FOUND (302), SEE_OTHER (303),TEMPORARY_REDIRECT (307), PERMANENT_REDIRECT (308) without 'Location' header|INTERNAL_SERVER_ERROR (500)
|All other status codes including UNAUTHORIZED (401) and FORBIDDEN (403)|NO_CONTENT (204) with Content URI in 'Content-Location' header
 
In all cases where the Location header is set, your HTTP client may redirect you immediately to the correct URL, so you probably won't recognize any difference compared to direct data access. If you receive status
 SERVICE_UNAVAILABLE (503) or INTERNAL_SERVER_ERROR (500) there is (currently) no chance to receive the data you've requested. If you receive status NO_CONTENT (204) you should check for the Content-Location header in order
to try to access the data manually. There are two situations where manual access might be promising: 

1. The remote server returned HTTP UNAUTHORIZED (401) or FORBIDDEN (403) as access requires custom authentication. If you own appropriate credentials, you can access the content after proper authentication.
2. If the content is not accessed via HTTP(s) you may use a custom data access client capable of opening a data stream to the content URI.

Beside of downloading single files, it's also possible to download all data of one resource or virtual subfolders. Let's assume you've organized a resource in the following way: 

```
> /
>> experiment
>>> parameters.txt
>>> measurements.csv
>>> reference_image.png
>> log
>>> output.log
>>> error.log
```

With this structure, your are able to dowload either the entire content by addressing '/', only all experiment data by addressing 'experiment' or only the 'log' folder. In order to do so, you just address a virtual folder the same way you
would address a single file, e.g. 

Download all content:

```bash
$ curl 'http://localhost:8080/api/v1/dataresources/56433955-2015-468c-b652-79657779bcf9/data/' -i -X GET \
    -H 'Accept: application/zip'
```

Download only experiment data:

```bash
$ curl 'http://localhost:8080/api/v1/dataresources/56433955-2015-468c-b652-79657779bcf9/data/experiment/' -i -X GET \
    -H 'Accept: application/zip'
```

Download only logs:

```bash
$ curl 'http://localhost:8080/api/v1/dataresources/56433955-2015-468c-b652-79657779bcf9/data/log/' -i -X GET \
    -H 'Accept: application/zip'
```

You can see, that the only differences compared to a single file download are the URLs ending with a slash, in order to address a virtual folder, and the provided content type in the 'Accept' header. In the example above, 'application/zip'
indicates that all content within the addressed folder is downloaded in a single ZIP archive. Currently, the following content types are supported: 

|Content Type|Format|Availability
|---|---|---
|application/zip|File with zip compression|Part of default KIT DM 2.0 instance
|application/vnd.datamanager.bagit+zip|BagIt file following the recommendations of the RDA Research Data Repository Interoperability Working Group with zip compression|Available via plugin (see [bagit-provider-plugin](https://github.com/kit-data-manager/bagit-provider-plugin))
 
