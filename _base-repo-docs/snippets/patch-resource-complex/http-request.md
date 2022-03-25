```http
PATCH /api/v1/dataresources/edbf964c-f215-4fc6-9ef1-2ff1ea5a811e HTTP/1.1
Content-Type: application/json-patch+json
If-Match: "-1248647055"
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