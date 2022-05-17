```http
PUT /api/v1/schemas/my_first_json HTTP/1.1
Content-Type: multipart/form-data; boundary=6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
If-Match: "-981854923"
Host: localhost:8040

--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
Content-Disposition: form-data; name=record; filename=schema-record4json-v4.json
Content-Type: application/json

{"schemaId":"my_first_json","pid":null,"schemaVersion":3,"label":null,"definition":null,"comment":null,"mimeType":"application/json","type":"JSON","createdAt":"2022-05-17T08:01:33Z","lastUpdate":"2022-05-17T08:01:34.324Z","acl":[{"id":1,"sid":"SELF","permission":"ADMINISTRATE"},{"id":null,"sid":"admin","permission":"ADMINISTRATE"}],"schemaDocumentUri":"http://localhost:8040/api/v1/schemas/my_first_json?version=3","schemaHash":"sha1:150dc302a01dbd35f360d4f09540fce859bfcd32","doNotSync":true}
--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm--
```