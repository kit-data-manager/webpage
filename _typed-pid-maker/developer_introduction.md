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

## Suggestions and contributions to the Typed PID Maker

The Typed PID Maker is developed openly on [our GitHub repository](https://github.com/kit-data-manager/pit-service). If you have a feature request or want to report a bug, please [open an issue](https://github.com/kit-data-manager/pit-service/issues/new/choose).

If you want to contribute code, consider our [contribution guidelines](https://github.com/kit-data-manager/pit-service/blob/master/CONTRIBUTING.md). All code contributions are licensed under the Apache 2.0 license. Our technology stack involves the Java programming language and the Spring Framework.
