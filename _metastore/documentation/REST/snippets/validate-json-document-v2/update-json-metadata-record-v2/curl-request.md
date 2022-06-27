```bash
$ curl 'http://localhost:8040/api/v1/metadata/6785ad43-9a17-40b5-9653-220a8232ef2f?version=1' -i -X PUT \
    -H 'Content-Type: multipart/form-data' \
    -H 'If-Match: "558661553"' \
    -F 'record=@metadata-record4json-v2.json;type=application/json' \
    -F 'document=@metadata-v2.json;type=application/xml' \
    -F 'version=1'
```