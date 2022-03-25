```http
PUT /api/v1/dataresources/edbf964c-f215-4fc6-9ef1-2ff1ea5a811e HTTP/1.1
Content-Type: application/json
If-Match: "495739650"
Content-Length: 1407
Host: localhost:8080

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
    "titleType" : "OTHER",
    "lang" : null
  } ],
  "publisher" : "KIT Data Manager",
  "publicationYear" : "2017",
  "resourceType" : {
    "id" : 1,
    "value" : "testingSample",
    "typeGeneral" : "DATASET"
  },
  "subjects" : [ ],
  "contributors" : [ ],
  "dates" : [ {
    "id" : 1,
    "value" : "2022-03-25T12:47:06Z",
    "type" : "CREATED"
  } ],
  "relatedIdentifiers" : [ ],
  "descriptions" : [ ],
  "geoLocations" : [ ],
  "language" : null,
  "alternateIdentifiers" : [ {
    "id" : 1,
    "value" : "edbf964c-f215-4fc6-9ef1-2ff1ea5a811e",
    "identifierType" : "INTERNAL"
  }, {
    "id" : 2,
    "value" : "resource-1-231118",
    "identifierType" : "OTHER"
  } ],
  "sizes" : [ ],
  "formats" : [ ],
  "version" : null,
  "rights" : [ ],
  "fundingReferences" : [ ],
  "lastUpdate" : "2022-03-25T12:47:07.152Z",
  "state" : "VOLATILE",
  "embargoDate" : null,
  "acls" : [ {
    "id" : 1,
    "sid" : "SELF",
    "permission" : "ADMINISTRATE"
  } ]
}
```