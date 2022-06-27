```bash
$ curl 'http://localhost:8040/api/v1/metadata' -i -X POST \
    -H 'Content-Type: multipart/form-data' \
    -F 'record=@metadata-record4json.json;type=application/json' \
    -F 'document=@metadata.json;type=application/json'
```