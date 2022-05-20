```bash
$ http --form PUT 'http://localhost:8040/api/v1/schemas/my_first_json' \
    'schema'@'schema-v2.json' \
    'If-Match:"1855465506"'
```