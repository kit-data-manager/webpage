```http
HTTP/1.1 200 OK
ETag: "-2010363665"
Resource-Version: 1
Content-Type: application/vnd.datamanager.content-information+json
Content-Length: 776

{
  "id" : 1,
  "parentResource" : {
    "id" : "edbf964c-f215-4fc6-9ef1-2ff1ea5a811e",
    "identifier" : {
      "value" : "(:tba)",
      "identifierType" : "DOI"
    },
    "alternateIdentifiers" : [ {
      "value" : "edbf964c-f215-4fc6-9ef1-2ff1ea5a811e",
      "identifierType" : "INTERNAL"
    } ]
  },
  "relativePath" : "randomFile.txt",
  "version" : 1,
  "fileVersion" : "1",
  "versioningService" : "simple",
  "depth" : 1,
  "contentUri" : "file:/tmp/repo-basepath/2022/2/25/edbf964cf2154fc69ef12ff1ea5a811e/randomFile.txt_1648212427612",
  "uploader" : "SELF",
  "mediaType" : "text/plain",
  "hash" : "sha1:4c29d7ed12eb7e0308a595ddaaf2b79a5a14bf2c",
  "size" : 64,
  "metadata" : { },
  "tags" : [ ],
  "filename" : "randomFile.txt"
}
```