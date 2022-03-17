```bash
$ curl 'http://localhost:8080/api/v1/dataresources/c9ddc646-e317-4d87-9ab8-a6be290e000d/data/randomFile2.txt' -i -X POST \
    -H 'Content-Type: multipart/form-data' \
    -F 'file=@randomFile2.txt;type=multipart/form-data' \
    -F 'metadata=@metadata.json;type=application/json'
```