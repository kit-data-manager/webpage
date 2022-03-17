```bash
$ curl 'http://localhost:8080/api/v1/dataresources/c9ddc646-e317-4d87-9ab8-a6be290e000d' -i -X PATCH \
    -H 'Content-Type: application/json-patch+json' \
    -H 'If-Match: "-851632841"' \
    -d '[ {
  "op" : "replace",
  "path" : "/publicationYear",
  "value" : "2017"
} ]'
```