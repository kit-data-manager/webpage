```http
HTTP/1.1 200 OK
ETag: "-851632841"
Resource-Version: 1
Content-Type: application/json
Content-Length: 1002

{
  "id" : "c9ddc646-e317-4d87-9ab8-a6be290e000d",
  "identifier" : {
    "id" : 1,
    "value" : "(:tba)",
    "identifierType" : "DOI"
  },
  "creators" : [ {
    "id" : 1,
    "familyName" : "Doe",
    "givenName" : "John",
    "affiliations" : [ "Karlsruhe Institute of Technology" ]
  } ],
  "titles" : [ {
    "id" : 1,
    "value" : "Most basic resource for testing",
    "titleType" : "OTHER"
  } ],
  "publisher" : "SELF",
  "publicationYear" : "2022",
  "resourceType" : {
    "id" : 1,
    "value" : "testingSample",
    "typeGeneral" : "DATASET"
  },
  "dates" : [ {
    "id" : 1,
    "value" : "2022-02-24T08:45:20Z",
    "type" : "CREATED"
  } ],
  "alternateIdentifiers" : [ {
    "id" : 1,
    "value" : "c9ddc646-e317-4d87-9ab8-a6be290e000d",
    "identifierType" : "INTERNAL"
  } ],
  "lastUpdate" : "2022-02-24T08:45:20.576Z",
  "state" : "VOLATILE",
  "acls" : [ {
    "id" : 1,
    "sid" : "SELF",
    "permission" : "ADMINISTRATE"
  } ]
}
```