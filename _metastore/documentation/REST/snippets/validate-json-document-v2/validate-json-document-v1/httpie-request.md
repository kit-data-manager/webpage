```bash
$ http --form POST 'http://localhost:8040/api/v1/schemas/my_first_json/validate?version=1' \
    'document'@'metadata-v2.json' \
    'version=1'
```