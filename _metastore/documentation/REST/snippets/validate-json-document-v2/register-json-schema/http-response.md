```http
HTTP/1.1 201 Created
Location: http://localhost:8040/api/v1/schemas/my_first_json?version=1
ETag: "1855465506"
Content-Type: application/json
Content-Length: 460

{
  "schemaId" : "my_first_json",
  "schemaVersion" : 1,
  "mimeType" : "application/json",
  "type" : "JSON",
  "createdAt" : "2022-05-20T09:54:01Z",
  "lastUpdate" : "2022-05-20T09:54:01.89Z",
  "acl" : [ {
    "id" : 1,
    "sid" : "SELF",
    "permission" : "ADMINISTRATE"
  } ],
  "schemaDocumentUri" : "http://localhost:8040/api/v1/schemas/my_first_json?version=1",
  "schemaHash" : "sha1:98741f0d6115474ab69375be3bc9cd5b305ce200",
  "doNotSync" : true
}
```