```bash
$ http --form PUT 'http://localhost:8040/api/v1/metadata/832baf8d-5c16-41a1-b4af-8d8538f73e8c?version=1' \
    'record'@'metadata-record4json-v2.json' \
    'document'@'metadata-v2.json' \
    'If-Match:"-399835742"' \
    'version=1'
```