```http
HTTP/1.1 200 OK
ETag: "1543949803"
Resource-Version: 1
Content-Type: application/json
Content-Length: 1002

{
  "id" : "edbf964c-f215-4fc6-9ef1-2ff1ea5a811e",
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
    "value" : "2022-03-25T12:47:06Z",
    "type" : "CREATED"
  } ],
  "alternateIdentifiers" : [ {
    "id" : 1,
    "value" : "edbf964c-f215-4fc6-9ef1-2ff1ea5a811e",
    "identifierType" : "INTERNAL"
  } ],
  "lastUpdate" : "2022-03-25T12:47:06.093Z",
  "state" : "VOLATILE",
  "acls" : [ {
    "id" : 1,
    "sid" : "SELF",
    "permission" : "ADMINISTRATE"
  } ]
}
```