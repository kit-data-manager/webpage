```
{
  "$schema" : "http://json-schema.org/draft/2019-09/schema#",
  "$id" : "http://www.example.org/schema/json",
  "type" : "object",
  "title" : "Json schema for tests",
  "default" : { },
  "required" : [ "title" ],
  "properties" : {
    "title" : {
      "$id" : "#/properties/string",
      "type" : "string",
      "title" : "Title",
      "description" : "Title of object."
    }
  },
  "additionalProperties" : false
}
```