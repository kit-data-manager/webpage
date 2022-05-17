```bash
$ curl 'http://localhost:8040/api/v1/schemas/my_first_json' -i -X PUT \
    -H 'Content-Type: multipart/form-data' \
    -H 'If-Match: "-981854923"' \
    -F 'record=@schema-record4json-v4.json;type=application/json'
```