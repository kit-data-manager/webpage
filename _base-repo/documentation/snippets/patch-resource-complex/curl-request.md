```bash
$ curl 'http://localhost:8080/api/v1/dataresources/edbf964c-f215-4fc6-9ef1-2ff1ea5a811e' -i -X PATCH \
    -H 'Content-Type: application/json-patch+json' \
    -H 'If-Match: "-1248647055"' \
    -d '[ {
  "op" : "add",
  "path" : "/alternateIdentifiers/1",
  "value" : {
    "identifierType" : "OTHER",
    "value" : "resource-1-231118"
  }
} ]'
```