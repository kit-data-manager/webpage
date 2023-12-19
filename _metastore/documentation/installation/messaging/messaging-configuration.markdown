---
title:  "Configuration of Messaging Feature"
breadcrumbs: /metastore/documentation/installation/messaging/configuration
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
categories: metastore messaging
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_instal
---

# {{ page.title }}

In order to make use of the messaging feature, a RabbitMQ instance must be running, preferably locally for security reasons. Please refer to the RabbitMQ web page [https://www.rabbitmq.com/]() on how to install and 
operate such an instance. From the repository perspective, all relevant settings are part of the default configuration file 'application.properties'. These properties, their function and values/defaults are listed 
in the following table. Typically, no additional repository-specific configuration of the message queue is necessary.

|property key|function|allowed values [default]
|----|----|----
|repo.messaging.enabled|Enables (true) or disables (false) the entire messaging functionality.|true or false [true]
|repo.messaging.hostname|The hostname where the RabbitMQ instance is running at.|A valid hostname [localhost]
|repo.messaging.port|The port on which the RabbitMQ instance is running at.|A numeric port number [5672]
|repo.messaging.username| Credential for RabbitMQ (username)|A string identifying user [guest]
|repo.messaging.password| Credemtial for RabbitMQ (password)|A string containing password for given user [guest]
|repo.messaging.sender.exchange|The RabbitMQ exchange to which all messages are sent.|A string uniquely identifying the exchange [metastore_events]
| **The following settings** | **are only needed by** | **receivers** 
|repo.messaging.receiver.exchange|The RabbitMQ exchange from where messages are received.|A string uniquely identifying the exchange [metastore_events]
|repo.messaging.receiver.queue|The name of the queue collecting all messages of the exchange. This queue is used for all handlers installed at the repository itself. External consumers may create an own quene.|A string uniquely identifying the queue [metastoreEventQueue]
|repo.messaging.receiver.routingKeys|The routing key (category.[subcategory] of messages) sent to the configured queue.|A string containing the category (e.g. 'metadata') and subcategory (e.g. '\#' for all) [metadata.\#]
|repo.schedule.rate|The schedule rate in milliseconds at which the repository checks for new messages.|A numeric amount of milliseconds [1000]

If you want to buld your own message handler please refer to the following [description](../../../../base-repo/documentation/messaging-handler.html)

<style>
td, th {
   border: none!important;
}
</style>
| [<< PREVIOUS](messaging-types-formats.html)|[NEXT >>](../index.html)|
|:----|----:|
| | |
