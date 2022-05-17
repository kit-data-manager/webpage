```bash
$ curl 'http://localhost:8040/api/v1/schemas' -i -X POST \
    -H 'Content-Type: multipart/form-data' \
    -F 'schema=@another-schema.json;type=application/xml' \
    -F 'record=@another-schema-record.json;type=application/json'
```