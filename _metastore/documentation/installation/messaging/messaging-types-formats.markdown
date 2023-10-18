---
title:  "Message Types and Formats"
breadcrumbs: /metastore/documentation/installation/messaging/messaging-types-formats
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
categories: metastore messaging
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_instal
---

# {{ page.title }}

There may different kinds of messages grouped by category. Depending on its category, a message may contain additional properties or not. The following table shows the currently available message categories and the 
condition under which a message with a certain category is sent.

|category[.subcategory].action|Sent if...
|----|----
|metadata.data.create|...a metadata document has been created. (POST to /api/v1/metadata)
|metadata.data.update|...a metadata document has been updated. (PUT to /api/v1/metadata/ID)
|metadata.data.delete|...a metadata document has been physically deleted (not implemented, yet).

 
Apart from the category (and an optional sub category) each message holds the associated resource identifier as 'entityId' as well as the caller as 'principal' and a timestamp when the message was created. In addition, all
messages in the 'data' subcategory also contain 'documentType' and 'resolvingUrl' information as 'metadata' in order to allow quick decisions on whether a message should be handled or not. 
The following snipped shows a sample message emitted after creating a new content element. 

```json
`{
  "principal": "SELF",
  "sender": "metastore-server",
  "timestamp": 1697547648298,
  "entityId": "e799b347-9ab8-4ec3-90df-b5257e90f5c6",
  "addressees": [],
  "action": "create",
  "subCategory": "data",
  "metadata": {
    "documentType": "http://localhost:8040/metastore/api/v1/schemas/simple?version=2",
    "resolvingUrl": "http://localhost:8040/metastore/api/v1/metadata/e799b347-9ab8-4ec3-90df-b5257e90f5c6?version=1"
  }
}
```

You will find all default elements mentioned above as well as the 'metadata' elements containing additional metadata specific to messages from the 'data' sub category. Messages are created by the repository as soon as the operation they are related to has successfully finished, jut before returning the result to the user. Therefor, a Message Queue service called RabbitMQ is used, which has to be installed in addition to the database 
and the repository microservice itself in order to be able to exchange messages.

<style>
td, th {
   border: none!important;
}
</style>
| [<< PREVIOUS](messaging-introduction.html)|[NEXT >>](messaging-configuration.html)|
|:----|----:|
| | |
