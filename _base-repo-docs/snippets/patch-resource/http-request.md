```http
PATCH /api/v1/dataresources/c9ddc646-e317-4d87-9ab8-a6be290e000d HTTP/1.1
Content-Type: application/json-patch+json
If-Match: "-851632841"
Content-Length: 81
Host: localhost:8080

[ {
  "op" : "replace",
  "path" : "/publicationYear",
  "value" : "2017"
} ]
```