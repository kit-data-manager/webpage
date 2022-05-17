```bash
$ curl 'http://localhost:8040/api/v1/schemas/my_first_json' -i -X PUT \
    -H 'Content-Type: multipart/form-data' \
    -H 'If-Match: "-626330405"' \
    -F 'schema=@schema-v3.json;type=application/json'
```