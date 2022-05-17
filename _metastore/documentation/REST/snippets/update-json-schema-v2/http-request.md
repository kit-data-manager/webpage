```http
PUT /api/v1/schemas/my_first_json HTTP/1.1
Content-Type: multipart/form-data; boundary=6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
If-Match: "1999717738"
Host: localhost:8040

--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm
Content-Disposition: form-data; name=schema; filename=schema-v2.json
Content-Type: application/json

{
    "$schema": "http://json-schema.org/draft/2019-09/schema#",
    "$id": "http://www.example.org/schema/json",
    "type": "object",
    "title": "Json schema for tests",
    "default": {},
    "required": [
        "title",
        "date"
    ],
    "properties": {
        "title": {
            "$id": "#/properties/string",
            "type": "string",
            "title": "Title",
            "description": "Title of object."
        },
        "date": {
            "$id": "#/properties/string",
            "type": "string",
            "format": "date",
            "title": "Date",
            "description": "Date of object"
        }
    },
    "additionalProperties": false
}
--6o2knFse3p53ty9dmcQvWAIx1zInP11uCfbm--
```