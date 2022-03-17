```http
PUT /api/v1/dataresources/c9ddc646-e317-4d87-9ab8-a6be290e000d HTTP/1.1
Content-Type: application/json
If-Match: "-1620739826"
Content-Length: 1407
Host: localhost:8080

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
    "value" : "2022-02-24T08:45:20Z",
    "type" : "CREATED"
  } ],
  "relatedIdentifiers" : [ ],
  "descriptions" : [ ],
  "geoLocations" : [ ],
  "language" : null,
  "alternateIdentifiers" : [ {
    "id" : 1,
    "value" : "c9ddc646-e317-4d87-9ab8-a6be290e000d",
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
  "lastUpdate" : "2022-02-24T08:45:21.516Z",
  "state" : "VOLATILE",
  "embargoDate" : null,
  "acls" : [ {
    "id" : 1,
    "sid" : "SELF",
    "permission" : "ADMINISTRATE"
  } ]
}
```