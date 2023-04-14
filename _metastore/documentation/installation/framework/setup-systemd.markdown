---
title:  Setup Service as Daemon (Debian)
breadcrumbs: /metastore/documentation/installation/framework/system
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_instal
---

# {{ page.title }} 

Systemd is now being used by many modern Linux distributions. 
To install a Spring Boot application as a systemd service, create a 'Unit File' 
named myapp.service and place it in /etc/systemd/system directory. 
The following 'Unit file' offers an example:

```
[Unit]
Description=myapp <-- Add your description here
After=syslog.target

[Service]
User=myapp <-- Add a valid user here. User MUST have access to jar file.
WorkingDirectory=/installation/path
ExecStart=/installation/path/'SERVICE'.jar <- jar file or shell script
SuccessExitStatus=143

[Install]
WantedBy=multi-user.target
```
--- 
NOTE
: If a startup script is available, it is recommended that you use it, as it may contain some additional settings. 

--- 

Note that, unlike when running as an init.d service, the user that runs the application, the PID file, and the console log file are managed by systemd itself and therefore must be configured by using appropriate fields in the ‘service’ script. Consult the service unit configuration man page for more details.

## Manage Service
```
root@server:~# systemctl start|stop|restart myapp(.service)
```
## Start Service at Startup
To flag the application to start automatically on system boot, use the following command:

```
root@server:~# systemctl enable myapp(.service)
```

For further details and/or other OS please refer to:
[Deploying Spring Boot Applications](https://docs.spring.io/spring-boot/docs/current/reference/html/deployment.html#deployment.installing)


<style>
td, th {
   border: none!important;
}
</style>
| [<< PREVIOUS](setup-metastore-service.html) |[NEXT >>](setup-apache-as-proxy.html)|
|:----|----:|
| | |
