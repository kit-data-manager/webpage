---
title:  Install (current) version of RabbitMQ (Debian/Ubuntu)
breadcrumbs: /metastore/documentation/installation/framework/rabbit
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_instal
---

# {{ page.title }} 
## Local

```
# Install dependencies 
root@server:~# apt-get install curl gnupg apt-transport-https -y

## Team RabbitMQ's main signing key
root@server:~# curl -1sLf "https://keys.openpgp.org/vks/v1/by-fingerprint/0A9AF2115F4687BD29803A206B73A36E6026DFCA" | gpg --dearmor | tee /usr/share/keyrings/com.rabbitmq.team.gpg > /dev/null

## Cloudsmith: modern Erlang repository
root@server:~# curl -1sLf https://dl.cloudsmith.io/public/rabbitmq/rabbitmq-erlang/gpg.E495BB49CC4BBE5B.key | gpg --dearmor | tee /usr/share/keyrings/io.cloudsmith.rabbitmq.E495BB49CC4BBE5B.gpg > /dev/null

## Cloudsmith: RabbitMQ repository
root@server:~# curl -1sLf https://dl.cloudsmith.io/public/rabbitmq/rabbitmq-server/gpg.9F4587F226208342.key | gpg --dearmor | tee /usr/share/keyrings/io.cloudsmith.rabbitmq.9F4587F226208342.gpg > /dev/null
```
Create file '/etc/apt/sources.list.d/rabbitmq.list' with following content:

--- 
NOTE
: On Ubuntu you have to replace 'deb/debian' by 'deb/ubuntu' and 'bullseye' by the distribution of your server (see /etc/os-release)

--- 
```
## Provides modern Erlang/OTP releases
##
deb [signed-by=/usr/share/keyrings/io.cloudsmith.rabbitmq.E495BB49CC4BBE5B.gpg] https://dl.cloudsmith.io/public/rabbitmq/rabbitmq-erlang/deb/debian bullseye main
deb-src [signed-by=/usr/share/keyrings/io.cloudsmith.rabbitmq.E495BB49CC4BBE5B.gpg] https://dl.cloudsmith.io/public/rabbitmq/rabbitmq-erlang/deb/debian bullseye main

## Provides RabbitMQ
##
deb [signed-by=/usr/share/keyrings/io.cloudsmith.rabbitmq.9F4587F226208342.gpg] https://dl.cloudsmith.io/public/rabbitmq/rabbitmq-server/deb/debian bullseye main
deb-src [signed-by=/usr/share/keyrings/io.cloudsmith.rabbitmq.9F4587F226208342.gpg] https://dl.cloudsmith.io/public/rabbitmq/rabbitmq-server/deb/debian bullseye main
```

```
root@server:~# apt-get update -y

# There may be an error message while starting rabbitmq-server. You can ignore this message. 
root@server:~# apt-get install -y erlang-base \
                        erlang-asn1 erlang-crypto erlang-eldap erlang-ftp erlang-inets \
                        erlang-mnesia erlang-os-mon erlang-parsetools erlang-public-key \
                        erlang-runtime-tools erlang-snmp erlang-ssl \
                        erlang-syntax-tools erlang-tftp erlang-tools erlang-xmerl
[...]

root@server:~# apt-get install rabbitmq-server -y --fix-missing
[...]

root@server:~# systemctl status rabbitmq-server
● rabbitmq-server.service - RabbitMQ broker
     Loaded: loaded (/lib/systemd/system/rabbitmq-server.service; enabled; vendor preset: enabled)
     Active: active (running) since [...]
```
## Docker
```
# latest RabbitMQ 3.11
docker run -it --rm --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3.11-management
```


<style>
td, th {
   border: none!important;
}
</style>
| [<< PREVIOUS](manage-elasticsearch.html)|[NEXT >>](setup-indexing-service.html)|
|:----|----:|
| | |
