```http
POST /api/v1/schemas/my_first_json/validate?version=1 HTTP/1.1
Content-Type: multipart/form-data; boundary=6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
Host: localhost:8040

--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
Content-Disposition: form-data; name=version

1
--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
Content-Disposition: form-data; name=document; filename=metadata-v3.json
Content-Type: application/json

{
"title": "My third JSON document",
"date": "2018-07-02",
"note": "since version 3 notes are allowed"
}
--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm--
```