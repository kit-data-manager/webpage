```http
HTTP/1.1 200 OK
Content-Type: application/vnd.datamanager.content-information+json
Content-Length: 2157

[ {
  "id" : 1,
  "parentResource" : {
    "id" : "c9ddc646-e317-4d87-9ab8-a6be290e000d",
    "identifier" : {
      "value" : "(:tba)",
      "identifierType" : "DOI"
    },
    "alternateIdentifiers" : [ {
      "value" : "c9ddc646-e317-4d87-9ab8-a6be290e000d",
      "identifierType" : "INTERNAL"
    } ]
  },
  "relativePath" : "randomFile.txt",
  "version" : 1,
  "fileVersion" : "1",
  "versioningService" : "simple",
  "depth" : 1,
  "contentUri" : "file:/tmp/repo-basepath/2022/1/24/c9ddc646-e317-4d87-9ab8-a6be290e000d/randomFile.txt_1645692321917",
  "uploader" : "SELF",
  "mediaType" : "text/plain",
  "hash" : "sha1:1a87ac39e8f8dd4cb264d9864ce32c6adf963d61",
  "size" : 64,
  "metadata" : { },
  "tags" : [ ],
  "filename" : "randomFile.txt"
}, {
  "id" : 2,
  "parentResource" : {
    "id" : "c9ddc646-e317-4d87-9ab8-a6be290e000d",
    "identifier" : {
      "value" : "(:tba)",
      "identifierType" : "DOI"
    },
    "alternateIdentifiers" : [ {
      "value" : "c9ddc646-e317-4d87-9ab8-a6be290e000d",
      "identifierType" : "INTERNAL"
    } ]
  },
  "relativePath" : "randomFile2.txt",
  "version" : 1,
  "fileVersion" : "1",
  "versioningService" : "none",
  "depth" : 1,
  "contentUri" : "file:/tmp/repo-basepath/2022/1/24/c9ddc646-e317-4d87-9ab8-a6be290e000d/randomFile2.txt_1645692322204",
  "mediaType" : "text/plain",
  "hash" : "sha1:1a87ac39e8f8dd4cb264d9864ce32c6adf963d61",
  "size" : 64,
  "metadata" : {
    "test" : "ok"
  },
  "tags" : [ ],
  "filename" : "randomFile2.txt"
}, {
  "id" : 3,
  "parentResource" : {
    "id" : "c9ddc646-e317-4d87-9ab8-a6be290e000d",
    "identifier" : {
      "value" : "(:tba)",
      "identifierType" : "DOI"
    },
    "alternateIdentifiers" : [ {
      "value" : "c9ddc646-e317-4d87-9ab8-a6be290e000d",
      "identifierType" : "INTERNAL"
    } ]
  },
  "relativePath" : "referencedContent",
  "version" : 1,
  "fileVersion" : "1",
  "versioningService" : "none",
  "depth" : 1,
  "contentUri" : "https://www.google.com",
  "size" : 0,
  "metadata" : { },
  "tags" : [ ],
  "filename" : "referencedContent"
} ]
```