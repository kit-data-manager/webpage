```http
PATCH /api/v1/dataresources/c9ddc646-e317-4d87-9ab8-a6be290e000d HTTP/1.1
Content-Type: application/json-patch+json
If-Match: "-850987930"
Content-Length: 152
Host: localhost:8080

[ {
  "op" : "add",
  "path" : "/alternateIdentifiers/1",
  "value" : {
    "identifierType" : "OTHER",
    "value" : "resource-1-231118"
  }
} ]
```