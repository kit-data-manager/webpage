```http
HTTP/1.1 200 OK
Location: http://localhost:8040/api/v1/metadata/832baf8d-5c16-41a1-b4af-8d8538f73e8c?version=3
ETag: "1671558446"
Content-Type: application/json
Content-Length: 692

{
  "id" : "832baf8d-5c16-41a1-b4af-8d8538f73e8c",
  "relatedResource" : {
    "identifier" : "https://repo/anyResourceId",
    "identifierType" : "URL"
  },
  "createdAt" : "2022-05-17T08:01:35Z",
  "lastUpdate" : "2022-05-17T08:01:35.756Z",
  "schema" : {
    "identifier" : "http://localhost:8040/api/v1/schemas/my_first_json?version=3",
    "identifierType" : "URL"
  },
  "schemaVersion" : 3,
  "recordVersion" : 3,
  "acl" : [ {
    "id" : 4,
    "sid" : "SELF",
    "permission" : "ADMINISTRATE"
  } ],
  "metadataDocumentUri" : "http://localhost:8040/api/v1/metadata/832baf8d-5c16-41a1-b4af-8d8538f73e8c?version=3",
  "documentHash" : "sha1:737762db675032231ac3cb872fccd32a83ac24d1"
}
```