```http
PATCH /api/v1/dataresources/edbf964c-f215-4fc6-9ef1-2ff1ea5a811e HTTP/1.1
Content-Type: application/json-patch+json
If-Match: "1543949803"
Content-Length: 81
Host: localhost:8080

[ {
  "op" : "replace",
  "path" : "/publicationYear",
  "value" : "2017"
} ]
```