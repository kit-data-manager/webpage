```bash
$ http --form PUT 'http://localhost:8040/api/v1/metadata/832baf8d-5c16-41a1-b4af-8d8538f73e8c' \
    'record'@'metadata-record4json-v3.json' \
    'document'@'metadata-v3.json' \
    'If-Match:"1192369073"'
```