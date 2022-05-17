```http
PUT /api/v1/metadata/832baf8d-5c16-41a1-b4af-8d8538f73e8c HTTP/1.1
Content-Type: multipart/form-data; boundary=6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
If-Match: "1192369073"
Host: localhost:8040

--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
Content-Disposition: form-data; name=record; filename=metadata-record4json-v3.json
Content-Type: application/json

{"id":"832baf8d-5c16-41a1-b4af-8d8538f73e8c","pid":null,"relatedResource":{"id":null,"identifier":"https://repo/anyResourceId","identifierType":"URL"},"createdAt":"2022-05-17T08:01:35Z","lastUpdate":"2022-05-17T08:01:35.393Z","schema":{"id":null,"identifier":"my_first_json","identifierType":"INTERNAL"},"schemaVersion":3,"recordVersion":1,"acl":[{"id":4,"sid":"SELF","permission":"ADMINISTRATE"}],"metadataDocumentUri":"http://localhost:8040/api/v1/metadata/832baf8d-5c16-41a1-b4af-8d8538f73e8c?version=1","documentHash":"sha1:97ac2fb17cd40aac07a55444dc161d615c70af8a"}
--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
Content-Disposition: form-data; name=document; filename=metadata-v3.json
Content-Type: application/xml

{
"title": "My third JSON document",
"date": "2018-07-02",
"note": "since version 3 notes are allowed"
}
--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm--
```