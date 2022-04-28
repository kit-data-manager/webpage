---
title:  "Configuration of Messaging Feature"
breadcrumbs: /base-repo/documentation/messaging-configuration
layout: default
categories: base-repo general
repository_url: https://github.com/kit-data-manager/base-repo
repository_name: kit-data-manager/base-repo
---

### {{ page.title }}

In order to make use of the messaging feature, a RabbitMQ instance must be running, preferably locally for security reasons. Please refer to the RabbitMQ web page [https://www.rabbitmq.com/]() on how to install and 
operate such an instance. From the repository perspective, all relevant settings are part of the default configuration file 'application.properties'. These properties, their function and values/defaults are listed 
in the following table. Typically, no additional repository-specific configuration of the message queue is necessary.

|property key|function|allowed values [default]
|----|----|----
|repo.messaging.enabled|Enables (true) or disables (false) the entire messaging functionality.|true or false [true]
|repo.messaging.hostname|The hostname where the RabbitMQ instance is running at.|A valid hostname [localhost]
|repo.messaging.port|The port on which the RabbitMQ instance is running at.|A numeric port number [5672]
|repo.messaging.sender.exchange|The RabbitMQ exchange to which all messages are sent.|A string uniquely identifying the exchange [repository_events]
|repo.messaging.receiver.exchange|The RabbitMQ exchange from where messages are received.|A string uniquely identifying the exchange [repository_events]
|repo.messaging.receiver.queue|The name of the queue collecting all messages of the exchange. This queue is used for all handlers installed at the repository itself. External consumers may create an own quene.|A string uniquely identifying the queue [repoEventQueue]
|repo.messaging.receiver.routingKeys|The routing key (category.[subcategory] of messages) sent to the configured queue.|A String containing the category (e.g. 'dataresource') and subcategory (e.g. '\#' for all) [dataresources.\#]
|repo.schedule.rate|The schedule rate in milliseconds at which the repository checks for new messages.|A numeric amount of milliseconds [1000]
