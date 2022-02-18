---
#layout: default
repository_url: https://github.com/kit-data-manager/base-repo
repository_name: kit-data-manager/base-repo
documentation_url: https://kit-data-manager.github.io/
description: A Generic, General Purpose Research Data Repository Service.
---

# The base-repo Service

The base-repo is a generic, general purpose research data repository service offering clear, machine-actionable RESTful interfaces for storing, retrieving and managing research data. Its purpose is to provide a low entrance barrier for research data management by keeping things as complex as necessary but as flexible as possible. Through the use of established technologies, i.e., software frameworks like Spring Boot, and broadly accepted standards, i.e., DataCite as base metadata standard, we provide a secure, maintainable and interoperable basis for entering the field of research data management.

## Features

* Light-weight microservice based on Spring Boot
* Easy installation, e.g., using available Docker images
* Full support of DataCite Standard 4.0
* Flexible organization of content in virtual folders
* Configurable versioning of metadata and content, e.g., following the OCFL specification
* (Optional) OAI-PMH support for metadata harvesting
* (Optional) Messaging support via RabbitMQ to process repository events, e.g., resource creation or file upload.
* (Optional) JWT-based autentication and authorization via Keycloak

## Additional Resources

<div class="downloads">
     <ul>
	 <span><li><a href="{{ page.repository_url }}"><img src="assets/images/github-brands.svg" style="height:20px; width:20px"/> Source Code</a></li></span>
	 <span><li><a href="{{ page.repository_url }}/issues"><img src="assets/images/bug-solid.svg" style="height:20px; width:20px"/> Issue Tracker</a></li></span>
	 <span><li><a href="{{ page.documentation_url }}"><img src="assets/images/book-solid.svg" style="height:20px; width:20px"/> Documentation</a></li></span>
	 </ul>
</div>


