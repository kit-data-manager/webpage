```http
POST /api/v1/schemas HTTP/1.1
Content-Type: multipart/form-data; boundary=6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
Host: localhost:8040

--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
Content-Disposition: form-data; name=schema; filename=another-schema.json
Content-Type: application/xml

{
    "$schema": "http://json-schema.org/draft/2019-09/schema#",
    "$id": "http://www.example.org/schema/json/example",
    "type": "object",
    "title": "Another Json schema for tests",
    "default": {},
    "required": [
        "description"
    ],
    "properties": {
        "description": {
            "$id": "#/properties/string",
            "type": "string",
            "title": "Description",
            "description": "Any description."
        }
    },
    "additionalProperties": false
}
--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
Content-Disposition: form-data; name=record; filename=another-schema-record.json
Content-Type: application/json

{"schemaId":"another_json","pid":null,"schemaVersion":null,"label":null,"definition":null,"comment":null,"mimeType":null,"type":"JSON","createdAt":null,"lastUpdate":null,"acl":[],"schemaDocumentUri":null,"schemaHash":null,"doNotSync":true}
--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm--
```