---
title:  "General Configuration"
breadcrumbs: /base-repo/documentation/general-configuration
layout: default
categories: base-repo general
repository_url: https://github.com/kit-data-manager/base-repo
repository_name: kit-data-manager/base-repo
navigation_id: base_repo_doc
---

### {{ page.title }}

For the base-repo, there are a couple of configuration options which are described here. All configuration is done in the file 'application.properties'. Spring Boot offers different ways of providing the configuration to a service. For base-repo, three options are relevant, whereas the current directory is the directory, where base-repo.jar is located:

1. In a /config subdir of the current directory.
2. In the current directory
3. Provided as command line argument -Dspring.config.location=[absolute path to application.properties]

Generally, all [listed properties](https://docs.spring.io/spring-boot/docs/current/reference/html/application-properties.html) offered by the Spring Framework are supported, but only a few of them are used by default. With the base-repo comes a default application.properties already containing all relevant properties with default values. Most of them can be changed according to local needs, properties which should not be changed are marked accordingly. For information on Spring properties, please refer to the official documentation.

Furthermore, there are several properties to configure the base-repo instance itself. For documentation of these properties, please refer to the configuration chapter of the according sub-system, e.g., auditing, messaging etc., or to the inline documentation in the sample application.properties.
