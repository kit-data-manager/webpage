---
title: Installation
breadcrumbs: /wap-server/documentation/
layout: default
description: A service for annotating digital content.
repository_url: https://github.com/kit-data-manager/wap-server
repository_name: kit-data-manager/wap-server
navigation_id: wap-server_index
---

# How to start

On this page, installation and configuration of the Web Application Protocol Server are described. 
All information you can find here are also available in the [source code repository at GitHub](https://github.com/kit-data-manager/wap-server/tree/master/howtos).

## Prerequisites

* git
* maven installed (tested 3.5.x)
* OpenJDK 8+

## Building the WAP Server

At first, you have to clone the software repository and change to the project folder: 

```
user@localhost:/home/user/$ git clone https://github.com/kit-data-manager/wap-server.git
[...]
user@localhost:/home/user/$ cd wap-server
user@localhost:/home/user/wap-server$
```

The build can now be started via: 

```
user@localhost:/home/user/wap-server$ mvn clean verify
[...]
```

Now, copy the final jar file from the *target/* folder to an empty folder in order to prepare the first start of the service.

```
user@localhost:/home/user/wap-server$ mkdir /home/user/wap-instance
user@localhost:/home/user/wap-server$ cp target/PSE-AA-0.0.1-SNAPSHOT.jar /home/user/wap-instance
[...]
```

---
**NOTE**
Please make sure, that the folder where you want to run the WAP Server from is empty. Otherwise, the installation procedure 
automatically performed on first startup won't work and has to be started manually by providing the argument *--install*
 in the next step.

---

In order to start the service, change to the service folder and call: 

```
user@localhost:/home/user/wap-server$ cd /home/user/wap-instance
user@localhost:/home/user/wap-server$ java -jar PSE-AA-0.0.1-SNAPSHOT.jar
Part found : PSE-AA-0.0.1-SNAPSHOT.jar!
Part found : PSE-AA-0.0.1-SNAPSHOT.jar!
#################################
### Starting installation
#################################
[...]
```

This will guide you through the installation of the service where you can initially configure your server. At the end of the process
you can either directly start the server or end the installation to adapt certain configuration properties, which can be found in the 
file *application.properties*, which was created by the installation procedure.

### Configuration Properties

| Property                              | Description                                                                                                                                                                                                                                                                                                                                                   | Default                         
|---------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------
| JsonLdCachedProfileValidityInMs       | The time in ms a cached JSON-LD profile is regarded up to date. If elapsed, the registry performs an update-download.                                                                                                                                                                                                                                         | 86400000                        
| ShouldAppendStackTraceToErrorMessages | Should stack traces be appended to http error messages. Of great help during debugging.                                                                                                                                                                                                                                                                       | false                           
| DataBasePath                          | The path where the database gets stored.                                                                                                                                                                                                                                                                                                                      | ./production_db                 
| EnableMandatorySlugInContainerPost    | Is the Slug header mandatory when creating containers via POST.                                                                                                                                                                                                                                                                                               | false                           
| EnableValidation                      | Is validation of Annotation and Container during POST active.                                                                                                                                                                                                                                                                                                 | true                            
| WebClientFolder                       | The folder where the web client is located.                                                                                                                                                                                                                                                                                                                   | /webcontent                     
| JsonLdProfileFolder                   | The folder where the JSON-LD profiles are locally cached.                                                                                                                                                                                                                                                                                                     | ./profiles                      
| SparqlReadIp                          | The IP of the SPARQL read-only endpoint. Either a specific one (including localhost) or * for all                                                                                                                                                                                                                                                             | *                               
| EnableContentNegotiation              | Is content negotiation active.                                                                                                                                                                                                                                                                                                                                | true                            
| SparqlReadPort                        | The port of the SPARQL read-only endpoint. Use -1 to disable this endpoint.                                                                                                                                                                                                                                                                                   | 3330                            
| FallbackValidation                    | Is fallback validation active. When posting elements in a format that has no specific validator implementation, the data is converted to JSON-LD and validated in this format before it gets posted.                                                                                                                                                          | true                            
| Hostname                              | The hostname under which this server can be reached. It has to be translated to the IP set in WapIp by DNS. This setting has influence on the root IRI and cannot be changed after a database has been created. For details refers to the Root Container section later.                                                                                       | localhost                       
| CorsAllowedOriginsPath                | The file where CORS allowed origins are stored. If the file does not exist on application startup, it is autocreated using the default setting to allow CORS for all origins. For details refers to the Cors section later.                                                                                                                                   | ./cors_allowed_origins.conf     
| WapIp                                 | The IP of the WAP endpoint. Either a specific one (including localhost) or * for all.                                                                                                                                                                                                                                                                         | *                               
| EnableMandatoryLabelInContainers      | Are labels mandatory when creating containers via POST.                                                                                                                                                                                                                                                                                                       | false                           
| JavaDocFolder                         | The folder where the javadoc is stored.                                                                                                                                                                                                                                                                                                                       | ./doc                           
| EnableHttps                           | Is HTTPS active. HTTPS has additional dependencies. This setting has influence on the root IRI and cannot be changed after a database has been created. For details refer so the SSL section later.                                                                                                                                                           | false                           
| JsonLdFrameFolder                     | The folder where the JSON-LD frames are stored.                                                                                                                                                                                                                                                                                                               | ./profiles                      
| JsonLdValidator_SchemaFolder          | The folder where the JSON-LD schemas are stored.                                                                                                                                                                                                                                                                                                              | ./schemas                       
| SimpleFormatters                      | The string configuring simple formats. For details refer to the Formats section later.                                                                                                                                                                                                                                                                        | NTRIPLES\*application/n-triples &#124; RDF_JSON\*application/rdf+json
| SparqlWritePort                       | The port of the SPARQL read-write endpoint. Use -1 to disable this endpoint.                                                                                                                                                                                                                                                                                  | 3331                            
| SparqlWriteIp                         | The IP of the SPARQL read-write endpoint. Either a specific one (including localhost) or * for all.                                                                                                                                                                                                                                                           | localhost                       
| PageSize                              | The count of annotations that lie within one PAGE in responses.                                                                                                                                                                                                                                                                                               | 20                              
| MultipleAnnotationPost                | Is posting multiple annotations in one request possible.                                                                                                                                                                                                                                                                                                      | true                            
| WapPort                               | The port under which the WAP service is reachable. This port is used for HTTP and HTTPS service. When 80 is set and a http service is used, the port is omitted. The same applies to HTTPS and port 443. This setting has influence on the root IRI and cannot be changed after a database has been created. For details refer to the Root Container section. | 80                              
| RdfBackendImplementation              | The qualifier of the used RDF backend implementation. The default backend is 'jena'.                                                                                                                                                                                                                                                                          | jena                            

### Root Container

Whenever the application is first started, the database is created using
a root container IRI that is determined from the configuration found at this time. It cannot be changed afterwards
because the root container IRI is a prefix to all stored elements IRIs. When it changes, they all would have to change.

The only way to get the application to work again is then to completely remove the database and have it recreated.
No access to any data created before exists then anymore.

The root container IRI is created using the following parameters:
- Hostname
- EnableHttps
- WapPort

Example 1: Hostname=localhost, EnableHttps=false, WapPort=8080
===> root IRI = http://localhost:8080/wap/

Example 2: Hostname=example.org, EnableHttps=false, WapPort=80
===> root IRI = http://example.org/wap/   (port is omitted because it is the default for HTTP)

Example 3: Hostname=localhost, EnableHttps=true, WapPort=1443
===> root IRI = https://localhost:1443/wap/

Example 4: Hostname=host1.example.org, EnableHttps=true, WapPort=443
===> root IRI = https://host1.example.org/wap/   (port is omitted because it is the default for HTTPS)

When using the installer (via --install or by starting the jar in an empty folder) it asks for this base configuration
and shows its consequences on the root container IRI.

If changing any of those parameters with an already running server is necessary, a deletion of the database is needed.
It gets recreated on first startup after the configuration has been changed.

---
**NOTE**
Using manual database manipulation, a conversion of the database to fit the new root container IRI can be achieved,
but this is not implemented in the application. The easiest way to achieve this would be to have the database
been backed up to NQUADS (which retains the named graphs) and then run a simple text replacement of old IRI ==> new IRI.
This has never been tested and should be regarded as a good starting point at best.

---

### Cross-Origin Resource Sharing (CORS)

Regarding CORS, there is only the option to specify the allowed hosts.
To configure this the file denoted in CorsAllowedOriginsPath (default = ./cors_allowed_origins.txt) is used.
If it is not found during application startup, it gets autocreated with the default value of allowing all hosts and has
the following content.

```
#default CORS allowed origins file, * means allow all
#www.example.org ==> allows http://www.example.org and https://www.example.org
*
```

If CORS should be disabled, either remove all lines from the file or comment out everything.
If a * is found, all other lines are ignored (since everything is then allowed anyway).

Only paths should be given and not the protocol like http and https.
Entering allowed.org leads to http://alowed.org and https://allowed.org to be acceptable.

The other parameters are all implemented in a fashion that is either explicitly * or resembles it in the best way.
- All requested methods are allowed (as long as the endpoint allows them in the usual Allow header)
- All headers present in the response are exposed.
- All headers are allowed to be used in requests. The server may reject/ignore the actual requests
  using these headers if the server has no idea what to do with them.

The actual requests then will be answered by an 403 if either CORS is disabled or the origin not allowed.
  
---
**NOTE**
The CORS configuration does not apply to direct SPARQL endpoints. Therefore, it is recommended not to make these endpoints publicly available.  

---

### SSL

To run the WAP Server with HTTPS, a valid key-store has to exist in a folder *./ssl/* relative to the server's installation folder.

Here are example steps that can be used with openssl to create a self-signed certificate for this purpose.
It has to be adapted to use officially signed certificates. Since these are usually created by provider-dependent tools,
consult the documentation of the registry selected to provide them.

Create key file, enter the key password twice. You are asked for a password, further written as **PrivateKeyPw**.

```
openssl genrsa -aes256 -out wap.key 4096
```

Create certificate file. numerous question getting asked. Either fill them appropriately or just accept defaults.
When asked for common name, you may provide the hostname you have entered before. This is not required.
The argument -days provides the validity in days.

```
openssl req -new -x509 -key wap.key -out wap.crt -days 3650
```

Convert the files to pkcs12 format. You are again asked for a password, further written as **KeyStorePw**.

```
openssl pkcs12 -inkey wap.key -in wap.crt -export -out wap.pkcs12
```

Finally, copy the keystore to *./ssl/* in case you did not execute the previous commands already in this directory.

Within the file *./ssl.conf* created during server installation, replace the values as needed. The default content
of the file is listed below:

```
key-store-file=wap.pkcs12
key-store-password=KeyStorePw
key-password=PrivateKeyPw
server.ssl.alias=1

```

The key alias is 1 if imported without any further options. if it does not fit or has been changed, adapt it.

#### Possible Questions

**Question** : I do not know the alias of the key ?
**Answer** : To list the aliases in a store type keytool -list -keystore .\wap.pkcs12

**Question** : I get a "cannot recover the key" Exception ?
**Answer** : There are some posts out there telling that the two passwords need to be the same
to solve this problem. We never had this issue.

### Formats

Simple formats are those that do have a Mimetype representation in Accept or Content-Type headers
that needs no additional processing. Examples ist TURTLE (text/turtle). A counter example would be JSON-LD including a profile.
Simple formats can be specified directly in the application.properties using the parameter SimpleFormatters.

Example SimpleFormatters=NTRIPLES\*application/n-triples &#124; RDF_JSON\*application/rdf+json

1. The String is split at the &#124;

- NTRIPLES\*application/n-triples
- RDF_JSON\*application/rdf+json

2. The parts then at the *

- NTRIPLES and application/n-triples
- RDF_JSON and application/rdf+json

The first part then must be identical to the Format name in the enum Formats (it gets determined by Formats.valueOf())
The second part is the String to recognize it in Accept/Content-Type.

- Format.NTRIPPLES and format String = application/n-triples
- Format.RDF_JSON and format String = applictaion/rdf+json

Since there is no way to further process any additional information in the format String this way, this can only be
done with these "simple formats"
