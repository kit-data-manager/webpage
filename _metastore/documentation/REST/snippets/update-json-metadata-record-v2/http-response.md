```http
HTTP/1.1 200 OK
Location: http://localhost:8040/api/v1/metadata/832baf8d-5c16-41a1-b4af-8d8538f73e8c?version=2
ETag: "1192369073"
Content-Type: application/json
Content-Length: 691

{
  "id" : "832baf8d-5c16-41a1-b4af-8d8538f73e8c",
  "relatedResource" : {
    "identifier" : "https://repo/anyResourceId",
    "identifierType" : "URL"
  },
  "createdAt" : "2022-05-17T08:01:35Z",
  "lastUpdate" : "2022-05-17T08:01:35.65Z",
  "schema" : {
    "identifier" : "http://localhost:8040/api/v1/schemas/my_first_json?version=2",
    "identifierType" : "URL"
  },
  "schemaVersion" : 2,
  "recordVersion" : 2,
  "acl" : [ {
    "id" : 4,
    "sid" : "SELF",
    "permission" : "ADMINISTRATE"
  } ],
  "metadataDocumentUri" : "http://localhost:8040/api/v1/metadata/832baf8d-5c16-41a1-b4af-8d8538f73e8c?version=2",
  "documentHash" : "sha1:1844c8057b673ae260fcc6b6ba146529b2b52771"
}
```