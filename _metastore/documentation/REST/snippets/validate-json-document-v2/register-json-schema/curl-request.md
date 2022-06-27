```bash
$ curl 'http://localhost:8040/api/v1/schemas' -i -X POST \
    -H 'Content-Type: multipart/form-data' \
    -F 'schema=@schema.json;type=application/json' \
    -F 'record=@schema-record4json.json;type=application/json'
```