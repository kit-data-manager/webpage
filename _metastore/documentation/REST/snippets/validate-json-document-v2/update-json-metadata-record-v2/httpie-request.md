```bash
$ http --form PUT 'http://localhost:8040/api/v1/metadata/6785ad43-9a17-40b5-9653-220a8232ef2f?version=1' \
    'record'@'metadata-record4json-v2.json' \
    'document'@'metadata-v2.json' \
    'If-Match:"558661553"' \
    'version=1'
```