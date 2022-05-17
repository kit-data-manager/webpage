```http
HTTP/1.1 200 OK
ETag: "1999717738"
Content-Type: application/vnd.datamanager.schema-record+json
Content-Length: 461

{
  "schemaId" : "my_first_json",
  "schemaVersion" : 1,
  "mimeType" : "application/json",
  "type" : "JSON",
  "createdAt" : "2022-05-17T08:01:33Z",
  "lastUpdate" : "2022-05-17T08:01:33.065Z",
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