```bash
$ curl 'http://localhost:8080/api/v1/dataresources/edbf964c-f215-4fc6-9ef1-2ff1ea5a811e/data/referencedContent' -i -X POST \
    -H 'Content-Type: multipart/form-data' \
    -F 'metadata=@metadata.json;type=application/json'
```