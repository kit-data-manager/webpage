```bash
$ curl 'http://localhost:8080/api/v1/dataresources/search' -i -X POST \
    -H 'Content-Type: application/json' \
    -d '{
  "id" : null,
  "identifier" : null,
  "creators" : [ ],
  "titles" : [ ],
  "publisher" : null,
  "publicationYear" : null,
  "resourceType" : {
    "id" : null,
    "value" : "testingSample",
    "typeGeneral" : "DATASET"
  },
  "subjects" : [ ],
  "contributors" : [ ],
  "dates" : [ ],
  "relatedIdentifiers" : [ ],
  "descriptions" : [ ],
  "geoLocations" : [ ],
  "language" : null,
  "alternateIdentifiers" : [ ],
  "sizes" : [ ],
  "formats" : [ ],
  "version" : null,
  "rights" : [ ],
  "fundingReferences" : [ ],
  "lastUpdate" : null,
  "state" : null,
  "embargoDate" : null,
  "acls" : [ ]
}'
```