```bash
$ echo '[ {
  "op" : "add",
  "path" : "/alternateIdentifiers/1",
  "value" : {
    "identifierType" : "OTHER",
    "value" : "resource-1-231118"
  }
} ]' | http PATCH 'http://localhost:8080/api/v1/dataresources/c9ddc646-e317-4d87-9ab8-a6be290e000d' \
    'Content-Type:application/json-patch+json' \
    'If-Match:"-850987930"'
```