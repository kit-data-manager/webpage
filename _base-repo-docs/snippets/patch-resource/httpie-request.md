```bash
$ echo '[ {
  "op" : "replace",
  "path" : "/publicationYear",
  "value" : "2017"
} ]' | http PATCH 'http://localhost:8080/api/v1/dataresources/edbf964c-f215-4fc6-9ef1-2ff1ea5a811e' \
    'Content-Type:application/json-patch+json' \
    'If-Match:"1543949803"'
```