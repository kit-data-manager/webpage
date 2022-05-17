```bash
$ http --form POST 'http://localhost:8040/api/v1/schemas' \
    'schema'@'another-schema.json' \
    'record'@'another-schema-record.json'
```