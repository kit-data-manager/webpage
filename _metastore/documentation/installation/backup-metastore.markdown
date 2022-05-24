---
title:  MetaStore (Backup)
breadcrumbs: /metastore/documentation/MetaStore (Backup)
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_instal
---

# {{ page.title }} 
MetaStore stores all related data (documents and datasets) in the following places:
- Folder for schema registry (see property metastore.schema.schemaFolder@application.properties)
- Folder for metadata documents (see property metastore.metadata.metadataFolder@application.properties)
- Database 'metastore' (see property spring.datasource.url@application.properties)

Please backup both folders and the database. 
