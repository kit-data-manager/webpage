---
title: Configuring the FAIR DO Lab
breadcrumbs: /typed-pid-maker/configuration
layout: default
description: Configuring single components.
repository_url: https://github.com/kit-data-manager/testbed4inf
repository_name: kit-data-manager/testbed4inf
navigation_id: fair_do_lab_index
---

# {{ page.title }}

As the Lab is a set of components, configuring it means to configure these components and its composition.

## Configure the component structure

The `docker-compose.yml` file defines ports and local hostnames of the services. It can be used to exclude services or include new ones.

## Configure the services

Each service has its own folder in the repository, containing configuration files like `Dockerfile`s, `application.properties` files, or more. They will be included either when building the image or when starting the container. While the `docker-compose.yml` sets for example hostnames and ports for each service, the communication between the services is being configured in the `appliation.properties` file of each service.

### Typed PID Maker

Configuration sub-folder: `pit-service`

Currently, there is no pre-built image of the Typed PID Maker. The configuration is included at build time of the image. This means to apply new configuration, you need to:

```bash
docker compose rm pit-service  # remove Typed PID Maker
docker compose build pit-service  # build new image
docker compose create pit-service  # create new container
```

Read more about [how to configure the Typed PID Maker (`application.properties`)](../typed-pid-maker/configuration.html). If you want to include your key and certificate files for configuration of a real PID prefix, you can put it into the `config` folder and refer to it in the `application.properties` via a relative path. Example: If you put the key in `config/key/keyfile.bin`, then use `key/keyfile.bin` to refer to it from the configuration file. If your file is password-protected, you can set the passphrase using the environment variable described in [the Typed PID Maker configuration description](../typed-pid-maker/configuration.html) within the `docker-compose.yml`.

## Indexer

Configuration sub-folder: `indexer`

Applying the configuration currently works the same as with the Typed PID Maker, described above. The following is a list of the most important properties in the `application.properties` file.

- `indexer.pit.resolvingURL: http://pit-service:8080/api/v1/pit/pid/%s`
    - A url to resolve a PID with a HTTP GET from a PIT service. This is because the messages the indexer receives contain PIDs, but it is the indexers choice how to resolve it.
    - Use `%s` as a placeholder for the PID to resolve.

- `indexer.recordMapping.mappingFiles: mytemplate`
    - A list of filenames, stored in the classpath (i.e. `java/main/resources`) which will be used to map the records into elastic-compatible json.
    - Example: `indexer.recordMapping.mappingFiles: mytemplate,yourtemplate` (Assuming your files are in the classpaths root and named `mytemplate.hbs` and `yourtemplate.hbs`)

- `indexer.elastic.folder: /elastic_json`
    - The subfolder where the json files, which are ingested into elasticsearch are stored locally. This might be useful as a backup.

- `indexer.elastic.baseUrl: http://elasticsearch:9200`
    - The base URL of the elasticsearch service, including port.

- `indexer.elastic.index: /record`
    - The elastic index ("database") where the records will be stored into.

The following properties define the communication with RabbitMQ.

- `repo.messaging.enabled: true`
    - Enables the messaging feature. The indexer will not work, if this is set to `false`.
- `repo.messaging.hostname: messagebroker`
    - Hostname of RabbitMQ.
- `repo.messaging.port: 5672`
    - Port of RabbitMQ
- `repo.messaging.receiver.exchange: record_events`
    - The exchange to listen to. This is the exchange where the Typed PID Maker puts its messages into.
- `repo.messaging.receiver.queue: indexerQueue`
    - The queue that will be registered for the indexer. Should be unique, except the plan is to have multiple indexers for parallelization.
- `repo.messaging.receiver.routingKeys: pidrecord.#`
    - The "routingKeys" or "topics" of the messages which should be indexed. The `#` is similar to `*` in regular expressions in this example. `pidrecord` is the topic prefix that the Typed PID Maker uses (e.g. `pidrecord.create`).

## Fairris

Configuration sub-folder: `fairris`

Fairris is a small user interface for *purely DEMO purposes*. It allows you to create and update minimalistic FAIR DOs using the Typed PID Maker. The current version has no configuration options.
