```http
PUT /api/v1/schemas/my_first_json HTTP/1.1
Content-Type: multipart/form-data; boundary=6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
If-Match: "-688555972"
Host: localhost:8040

--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
Content-Disposition: form-data; name=record; filename=schema-record4json-v4.json
Content-Type: application/json

{"schemaId":"my_first_json","pid":null,"schemaVersion":2,"label":null,"definition":null,"comment":null,"mimeType":"application/json","type":"JSON","createdAt":"2022-05-20T09:54:01Z","lastUpdate":"2022-05-20T09:54:02.753Z","acl":[{"id":1,"sid":"SELF","permission":"ADMINISTRATE"},{"id":null,"sid":"admin","permission":"ADMINISTRATE"}],"schemaDocumentUri":"http://localhost:8040/api/v1/schemas/my_first_json?version=2","schemaHash":"sha1:68c72ab169770015f9b68645d0a50ac33a98f46c","doNotSync":true}
--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm--
```