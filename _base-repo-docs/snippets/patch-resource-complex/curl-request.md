```bash
$ curl 'http://localhost:8080/api/v1/dataresources/c9ddc646-e317-4d87-9ab8-a6be290e000d' -i -X PATCH \
    -H 'Content-Type: application/json-patch+json' \
    -H 'If-Match: "-850987930"' \
    -d '[ {
  "op" : "add",
  "path" : "/alternateIdentifiers/1",
  "value" : {
    "identifierType" : "OTHER",
    "value" : "resource-1-231118"
  }
} ]'
```