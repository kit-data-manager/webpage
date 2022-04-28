---
title:  "Message Types and Formats"
breadcrumbs: /base-repo/documentation/messaging-types-formats
layout: default
categories: base-repo messaging
repository_url: https://github.com/kit-data-manager/base-repo
repository_name: kit-data-manager/base-repo
---

### {{ page.title }}

There are different kinds of messages grouped by category. Depending on its category, a message may contain additional properties or not. The following table shows all currently available message categories and the 
condition under which a message with a certain category is sent.

|category[.subcategory]|Sent if...
|----|----
|create|...a data resource has been created.
|create.data|...a new content element has been uploaded.
|update|...a data resource has been updated via PUT or PATCH.
|update.data|...the metadata of a content element has been updated via PATCH.
|update.acl|...an access control list element of a data resource has been updated via PATCH.
|delete|...a data resource has been physically deleted (not implemented, yet).
|delete.data|...a content element has been deleted.
|fix|...a data resource has been changed to FIXED state.
|revoke|...a data resource has been changed to REVOKED state.

 
Apart from the category (and an optional sub category) each message holds the associated resource identifier as 'entityId' as well as the caller as 'principal' and a timestamp when the message was created. In addition, all
messages in the 'data' subcategory also contain 'contentPath', 'contentUri' and 'contentType' information as 'metadata' in order to allow quick decisions on whether a message should be handled or not. 
The following snipped shows a sample message emitted after creating a new content element. 

```json
{
"principal":"SELF",
"sender":"localhost",
"timestamp":1551963353619,
"entityId":"test123",
"action":"create",
"subCategory":"data",
"metadata":
{
"contentPath":"folder/image.png",
"contentUri":"file:///mnt/data/repository/2019/test123/image.png_1234412332",
"contentType":"image/png"
}
}
````

You will find all default elements mentioned above as well as the 'metadata' elements containing additional metadata specific to messages from the 'data' sub category. Messages are created by the repository as soon as 
the operation they are related to has successfully finished, jut before returning the result to the user. Therefor, a Message Queue service called RabbitMQ is used, which has to be installed in addition to the database 
and the repository microservice itself in order to be able to exchange messages.
