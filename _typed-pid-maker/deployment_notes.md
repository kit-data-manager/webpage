---
title: Deployment Notes for the Typed PID Maker
breadcrumbs: /typed-pid-maker/installation
layout: default
description: Important notes to consider for deployments.
repository_url: https://github.com/kit-data-manager/pit-service
repository_name: kit-data-manager/pit-service
navigation_id: typed_pid_maker_index
---

# Deployment Notes

This document adds information beyond the installation and configuration of the Typed PID Maker.

## Request Timeouts

Some requests to the Typed PID Maker may have heavily varying response times. This is caused by the validation functionality. If the internal cache does not have required information available (e.g. because it is outdated or has never been requested before), requests have to be made to the configured Data Type Registry (DTR). These requests currently consume some time. Such a "heavy request" may take around 30+ seconds. If the cache is filled, the same requests usually finish in under a second.

**The issue** occurs when using other technologies in front of the Typed PID Maker, like a HTTP reverse-proxy. They may time out with their default configuration.

**Affected** is Version 2.0.0 or lower.

**The mitigation** for now is to raise the timeout to more than 30 seconds. We recommend 60 seconds to be on the safe side.

**In the long term**, we plan to resolve this performance issue by optimizing the way we process requests (asynchronous execution). But it requires some time.
