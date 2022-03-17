```bash
$ curl 'http://localhost:8080/api/v1/dataresources/c9ddc646-e317-4d87-9ab8-a6be290e000d/data/referencedContent' -i -X POST \
    -H 'Content-Type: multipart/form-data' \
    -F 'metadata=@metadata.json;type=application/json'
```