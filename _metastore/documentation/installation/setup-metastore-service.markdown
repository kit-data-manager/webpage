---
title:  Setup Metastore Service (Debian)
breadcrumbs: /metastore/documentation/installation
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_instal
---

# {{ page.title }} 
To setup a service you have to execute the following steps:
## Install Apache as a Proxy Server
It's recommended to install a proxy server accessing the service.
In this example Apache is used but you may also use 'nginx' for this task.

Replace ***'SERVICE'*** by the name of your service. (e.g.: metastore)

Replace ***'FQDN'*** with the fully qualified domain name of the server. (e.g. server.example.org)
```
root@server:~# apt update
[...]
root@server:~# apt install apache2
[...]
root@server:~# apache2 -v
Server version: Apache/2.4.52 (Debian)
Server built:   2022-01-03T21:27:14
root@server:~# systemctl status apache2.service
● apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
     Active: active (running) since [...]
```

### Configure Proxy for Service
```
root@server:~# cd /etc/apache2/sites-available/
root@server:/etc/apache2/sites-available/# cp 000-default.conf  'SERVICE'.conf
[...]
root@server:/etc/apache2/sites-available/# joe 'SERVICE'.conf
        ServerName 'FQDN'
[...]
root@server:/etc/apache2/sites-available/# a2ensite 'SERVICE'.conf
[...]
root@server:/etc/apache2/sites-available/# systemctl reload apache2
[...]
root@server:/etc/apache2/sites-available/# 
[...]
```
### Create Certificate for Server
Since a service should at least be secured via https, a certificate is required first.
If no server certificate exists you have to create a certificat first.
In the meantime, there are scripts for the installation of a certificate and its management, 
which simplify the installation much more.

NOTE
: To use the scripts the server ports 80 and 443 should be accessible from everywhere.

```
root@server:~# apt install certbot python3-certbot-nginx
[...]
root@server:~# apt install python3-certbot-apache
[...]
root@server:~# certbot --apache -d 'FQDN'
[...]
root@server:~# systemctl status certbot.timer
● certbot.timer - Run certbot twice daily
     Loaded: loaded (/lib/systemd/system/certbot.timer; enabled; vendor preset: enabled)
     Active: active (waiting) [...]
root@server:~# certbot renew --dry-run
[...]
Congratulations, all simulated renewals succeeded: 
  /etc/letsencrypt/live/'FQDN'/fullchain.pem (success)
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
```

## Build Service
In case of a SpringBoot service a bootable jar file is recommended.
If no further informations available you may build a jar file
by typing
```
root@server:~# bash ./gradlew bootJar
> Configure project :
[...]
```
Create a directory for the service:
```
root@server:~# mkdir -p /installation/path/
```
Copy jar file to service directory:
```
root@server:~# cp build/libs/'SERVICE'-VERSION.jar /installation/path/
# Don't overwrite 'old' versions. Use soft links to redirect to newest version. 
root@server:~# ln -s /installation/path/'SERVICE'-VERSION.jar /installation/path/'SERVICE'.jar
```
NOTE
: Bootable jars myare not compatible to all OS.

Create 'application.properties' and adjust it to your needs (optional):
```
root@server:~# vi /installation/path/application.properties
[...]
```
## Create Keystore for Service
To make the certificate available to a service it has to be stored in a keystore.
```
# Switch to directory holding the certificates
root@server:~# cd /etc/letsencrypt/archive/'FQDN'
# Look for the current certificate (cert*.pem, privkey*.pem, chain*.pem)
# e.g.: 1
# Create keystore
root@server:~# openssl pkcs12 -export -in cert1.pem -inkey privkey1.pem -out keystore_1.p12 -name 'FQDN' -CAfile chain1.pem -caname root -password pass:'PASSWORD_KEYSTORE'
# Copy keystore to certain directory
root@server:~# cp keystore_1.p12 /etc/letsencrypt/keystore
root@server:~# chmod 644 /etc/letsencrypt/keystore/keystore_1.p12
root@server:~# ln -s /etc/letsencrypt/keystore/keystore_1.p12 /etc/letsencrypt/keystore/keystore.p12
```
NOTE
: Every time when certificate has been updated the service has to be restarted. (systemctl restart 'SERVICE')
: Since certificates have a limited expiration date, this process must be repeated at regular intervals.

## Enabling HTTPS for Service
To enable https for SpringBoot services you have to extend the application.properties file.
To do so without touching the original configuration you have to create the file 'application.properties'
in the subfolder 'config'. The file should look like this:
```
config/application.properties
=============================
# This file overwrites/extends the settings defined in ../application.properties

###############################################################################
# Server settings
###############################################################################
# Port
###############################################################################
server.port: 8443
###############################################################################
# SSL
###############################################################################
# The format used for the keystore.
server.ssl.key-store-type: pkcs12
# The path to the keystore containing the certificate
server.ssl.key-store: /etc/letsencrypt/keystore/keystore.p12
# The password used to generate the certificate
server.ssl.key-store-password: 'PASSWORD_KEYSTORE'
# The alias mapped to the certificate
server.ssl.key-alias: 'FQDN'
server.ssl.key-password: 'PASSWORD_KEYSTORE'
```

## Configure Proxy for HTTPS
To enable service via proxy an additional proxy file is needed:
```
/etc/apache2/sites-available/'SERVICE'-ssl.conf
===============================================
<IfModule mod_ssl.c>
<VirtualHost *:443>
        [...]
        ServerName  'FQDN'
        ServerAlias 'FQDN'
        [...]
        #################################################
        # Configuration for Reverse Proxy
        #################################################
        SSLEngine on
        SSLProxyEngine On
        ProxyPreserveHost On
        ProxyPass / https://0.0.0.0:8443/
        ProxyPassReverse / https://0.0.0.0:8443/

        SSLCertificateFile /etc/letsencrypt/live/'FQDN'/fullchain.pem
        SSLCertificateKeyFile /etc/letsencrypt/live/'FQDN'/privkey.pem
        Include /etc/letsencrypt/options-ssl-apache.conf
</VirtualHost>
</IfModule>
```
To enable these settings you have to create a softlink to this file in
folder '/etc/apache2/sites-enabled'
```
root@server:~# ln -s /etc/apache2/sites-available/'SERVICE'-ssl.conf /etc/apache2/sites-enabled/'SERVICE'-ssl.conf
```
Restart apache server
```
root@server:~# systemctl restart apache2
```

For further Information how to Configure Apache Proxy (for SSL)
- [Configure Proxy (apache2)](https://httpd.apache.org/docs/2.4/howto/reverse_proxy.html)
- [Configure Proxy (How to)](https://www.middlewareinventory.com/blog/apache-reverse-proxy-what-how-to-configure-setup-reverse-proxy/)
- [Configure Proxy using Siny server as example](https://www.r-bloggers.com/2015/12/shiny-https-securing-shiny-open-source-with-ssl/)


## Installation as a systemd Service

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


