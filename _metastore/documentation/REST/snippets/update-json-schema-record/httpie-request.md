```bash
$ http --form PUT 'http://localhost:8040/api/v1/schemas/my_first_json' \
    'record'@'schema-record4json-v4.json' \
    'If-Match:"-981854923"'
```