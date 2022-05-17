```bash
$ curl 'http://localhost:8040/api/v1/schemas/my_first_json/validate' -i -X POST \
    -H 'Content-Type: multipart/form-data' \
    -F 'document=@metadata-v3.json;type=application/json'
```