```http
HTTP/1.1 200 OK
Location: http://localhost:8040/api/v1/schemas/my_first_json?version=3
ETag: "-981854923"
Content-Type: application/json
Content-Length: 461

{
  "schemaId" : "my_first_json",
  "schemaVersion" : 3,
  "mimeType" : "application/json",
  "type" : "JSON",
  "createdAt" : "2022-05-17T08:01:33Z",
  "lastUpdate" : "2022-05-17T08:01:34.324Z",
  "acl" : [ {
    "id" : 1,
    "sid" : "SELF",
    "permission" : "ADMINISTRATE"
  } ],
  "schemaDocumentUri" : "http://localhost:8040/api/v1/schemas/my_first_json?version=3",
  "schemaHash" : "sha1:150dc302a01dbd35f360d4f09540fce859bfcd32",
  "doNotSync" : true
}
```