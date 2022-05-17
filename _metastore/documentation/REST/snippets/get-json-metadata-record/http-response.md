```http
HTTP/1.1 200 OK
ETag: "-399835742"
Content-Type: application/vnd.datamanager.metadata-record+json
Content-Length: 692

{
  "id" : "832baf8d-5c16-41a1-b4af-8d8538f73e8c",
  "relatedResource" : {
    "identifier" : "https://repo/anyResourceId",
    "identifierType" : "URL"
  },
  "createdAt" : "2022-05-17T08:01:35Z",
  "lastUpdate" : "2022-05-17T08:01:35.393Z",
  "schema" : {
    "identifier" : "http://localhost:8040/api/v1/schemas/my_first_json?version=1",
    "identifierType" : "URL"
  },
  "schemaVersion" : 1,
  "recordVersion" : 1,
  "acl" : [ {
    "id" : 4,
    "sid" : "SELF",
    "permission" : "ADMINISTRATE"
  } ],
  "metadataDocumentUri" : "http://localhost:8040/api/v1/metadata/832baf8d-5c16-41a1-b4af-8d8538f73e8c?version=1",
  "documentHash" : "sha1:97ac2fb17cd40aac07a55444dc161d615c70af8a"
}
```