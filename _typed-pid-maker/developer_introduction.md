---
title: Usage and contributions
breadcrumbs: /typed-pid-maker/developer_introduction
layout: default
description: A quick guide into the usage and internals of the Typed PID Maker.
repository_url: https://github.com/kit-data-manager/pit-service
repository_name: kit-data-manager/pit-service
navigation_id: typed_pid_maker_index
---

# {{ page.title }}

This article targets developers and potential contributors. If you like to cite this software, the ["Cite this repository" button on the right side on GitHub](https://github.com/kit-data-manager/pit-service) will be helpful for you. The information in there is generated from [the file `citation.cff`](https://github.com/kit-data-manager/pit-service/blob/master/CITATION.cff).

## Developing applications using a Typed PID Maker instance

The Typed PID Maker offers a REST interface to use for other applications. The API for a specific instance depends partially on its configuration details. Therefore, the best documentation is the one it offers at runtime (openAPI/swagger) at `$domain:$port/swagger-ui.html` (for example <http://localhost:8090/swagger-ui.html>).

We keep the [API documentation on our webpage](openapi.html) up-to-date, so it should always reflect the API of the newest version. Again, note some APIs might not be available depending on the configuration.

### Search example

The Typed PID Maker exposes the search interface of Elasticsearch through its REST interface, if it is configured to do so. For testing purposes, the search can also be executed via the provided swagger interface (default location: <http://localhost:8090/swagger-ui.html>). For example, with the following request body you will get all record information:

```json
{
  "query": {
    "regexp": {
      "pid": {
        "value": ".*",
        "flags": "ALL",
        "case_insensitive": true
      }
    }
  }
}
```

You can also use other http clients, like CURL. A CURL request (which may be provided by swagger) may look like this:

```bash
curl -X 'POST' \
  'http://localhost:8090/api/v1/search?page=0&size=20' \
  -H 'accept: application/hal+json' \
  -H 'Content-Type: application/json' \
  -d '{
  "query": {
    "regexp": {
      "pid": {
        "value": ".*",
        "flags": "ALL",
        "case_insensitive": true
      }
    }
  }
}'
```

The records are stored in a search index called `typedpidmaker`. There is an extensive [documentation of the Elastic query language](https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl.html).

## Suggestions and contributions to the Typed PID Maker

The Typed PID Maker is developed openly on [our GitHub repository](https://github.com/kit-data-manager/pit-service). If you have a feature request or want to report a bug, please [open an issue](https://github.com/kit-data-manager/pit-service/issues/new/choose).

If you want to contribute code, consider our [contribution guidelines](https://github.com/kit-data-manager/pit-service/blob/master/CONTRIBUTING.md). All code contributions are licensed under the Apache 2.0 license. Our technology stack involves the Java programming language and the Spring Framework.
