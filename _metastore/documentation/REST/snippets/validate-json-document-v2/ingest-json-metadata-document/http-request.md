```http
POST /api/v1/metadata HTTP/1.1
Content-Type: multipart/form-data; boundary=6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
Host: localhost:8040

--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
Content-Disposition: form-data; name=record; filename=metadata-record4json.json
Content-Type: application/json

{"id":null,"pid":null,"relatedResource":{"id":null,"identifier":"https://repo/anyResourceId","identifierType":"URL"},"createdAt":null,"lastUpdate":null,"schema":{"id":null,"identifier":"my_first_json","identifierType":"INTERNAL"},"schemaVersion":1,"recordVersion":null,"acl":[],"metadataDocumentUri":null,"documentHash":null}
--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
Content-Disposition: form-data; name=document; filename=metadata.json
Content-Type: application/json

{
"title": "My first JSON document"
}
--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm--
```