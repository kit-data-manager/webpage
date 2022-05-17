```
{
  "$schema" : "http://json-schema.org/draft/2019-09/schema#",
  "$id" : "http://www.example.org/schema/json",
  "type" : "object",
  "title" : "Json schema for tests",
  "default" : { },
  "required" : [ "title", "date" ],
  "properties" : {
    "title" : {
      "$id" : "#/properties/string",
      "type" : "string",
      "title" : "Title",
      "description" : "Title of object."
    },
    "date" : {
      "$id" : "#/properties/string",
      "type" : "string",
      "format" : "date",
      "title" : "Date",
      "description" : "Date of object"
    },
    "note" : {
      "$id" : "#/properties/string",
      "type" : "string",
      "title" : "Note",
      "description" : "Additonal information about object"
    }
  },
  "additionalProperties" : false
}
```