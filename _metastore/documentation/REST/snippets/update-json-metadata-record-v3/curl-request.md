```bash
$ curl 'http://localhost:8040/api/v1/metadata/832baf8d-5c16-41a1-b4af-8d8538f73e8c' -i -X PUT \
    -H 'Content-Type: multipart/form-data' \
    -H 'If-Match: "1192369073"' \
    -F 'record=@metadata-record4json-v3.json;type=application/json' \
    -F 'document=@metadata-v3.json;type=application/xml'
```