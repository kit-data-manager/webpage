```bash
$ curl 'http://localhost:8040/api/v1/metadata/832baf8d-5c16-41a1-b4af-8d8538f73e8c?version=1' -i -X PUT \
    -H 'Content-Type: multipart/form-data' \
    -H 'If-Match: "-399835742"' \
    -F 'record=@metadata-record4json-v2.json;type=application/json' \
    -F 'document=@metadata-v2.json;type=application/xml' \
    -F 'version=1'
```