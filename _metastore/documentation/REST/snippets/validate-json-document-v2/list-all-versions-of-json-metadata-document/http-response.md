```http
HTTP/1.1 200 OK
Content-Range: 0-9/2
Content-Type: application/json
Content-Length: 1389

[ {
  "id" : "6785ad43-9a17-40b5-9653-220a8232ef2f",
  "relatedResource" : {
    "identifier" : "https://repo/anyResourceId",
    "identifierType" : "URL"
  },
  "createdAt" : "2022-05-20T09:54:03Z",
  "lastUpdate" : "2022-05-20T09:54:03.677Z",
  "schema" : {
    "identifier" : "http://localhost:8040/api/v1/schemas/my_first_json?version=2",
    "identifierType" : "URL"
  },
  "schemaVersion" : 2,
  "recordVersion" : 2,
  "acl" : [ {
    "id" : 3,
    "sid" : "SELF",
    "permission" : "ADMINISTRATE"
  } ],
  "metadataDocumentUri" : "http://localhost:8040/api/v1/metadata/6785ad43-9a17-40b5-9653-220a8232ef2f?version=2",
  "documentHash" : "sha1:1844c8057b673ae260fcc6b6ba146529b2b52771"
}, {
  "id" : "6785ad43-9a17-40b5-9653-220a8232ef2f",
  "relatedResource" : {
    "identifier" : "https://repo/anyResourceId",
    "identifierType" : "URL"
  },
  "createdAt" : "2022-05-20T09:54:03Z",
  "lastUpdate" : "2022-05-20T09:54:03.45Z",
  "schema" : {
    "identifier" : "http://localhost:8040/api/v1/schemas/my_first_json?version=1",
    "identifierType" : "URL"
  },
  "schemaVersion" : 1,
  "recordVersion" : 1,
  "acl" : [ {
    "id" : 3,
    "sid" : "SELF",
    "permission" : "ADMINISTRATE"
  } ],
  "metadataDocumentUri" : "http://localhost:8040/api/v1/metadata/6785ad43-9a17-40b5-9653-220a8232ef2f?version=1",
  "documentHash" : "sha1:97ac2fb17cd40aac07a55444dc161d615c70af8a"
} ]
```