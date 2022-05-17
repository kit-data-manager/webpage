```bash
$ curl 'http://localhost:8040/api/v1/schemas/my_first_json' -i -X PUT \
    -H 'Content-Type: multipart/form-data' \
    -H 'If-Match: "1999717738"' \
    -F 'schema=@schema-v2.json;type=application/json'
```