```http
PUT /api/v1/metadata/6785ad43-9a17-40b5-9653-220a8232ef2f?version=1 HTTP/1.1
Content-Type: multipart/form-data; boundary=6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
If-Match: "558661553"
Host: localhost:8040

--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
Content-Disposition: form-data; name=version

1
--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
Content-Disposition: form-data; name=record; filename=metadata-record4json-v2.json
Content-Type: application/json

{"id":"6785ad43-9a17-40b5-9653-220a8232ef2f","pid":null,"relatedResource":{"id":null,"identifier":"https://repo/anyResourceId","identifierType":"URL"},"createdAt":"2022-05-20T09:54:03Z","lastUpdate":"2022-05-20T09:54:03.45Z","schema":{"id":null,"identifier":"my_first_json","identifierType":"INTERNAL"},"schemaVersion":2,"recordVersion":1,"acl":[{"id":3,"sid":"SELF","permission":"ADMINISTRATE"}],"metadataDocumentUri":"http://localhost:8040/api/v1/metadata/6785ad43-9a17-40b5-9653-220a8232ef2f?version=1","documentHash":"sha1:97ac2fb17cd40aac07a55444dc161d615c70af8a"}
--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
Content-Disposition: form-data; name=document; filename=metadata-v2.json
Content-Type: application/xml

{
"title": "My second JSON document",
"date": "2018-07-02"
}
--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm--
```