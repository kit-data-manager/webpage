---
title:  Backups
breadcrumbs: /metastore/documentation/framework/MetaStore (Backup)
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_instal
---

# {{ page.title }} 
## MetaStore
MetaStore stores all related data (documents and datasets) in the following places:
- Folder for schema registry (see property metastore.schema.schemaFolder@application.properties)
- Folder for metadata documents (see property metastore.metadata.metadataFolder@application.properties)
- Database 'metastore' (see property spring.datasource.url@application.properties)

Please backup both folders and the database. 

## Indexing Service
The indexing-service stores all related data (mappings and related records) in the following places:
- Folder for mapping (see property metastore.indexer.mappingsLocation@application.properties)
- Database 'indexing' (see property spring.datasource.url@application.properties)

Please backup mapping folder and the database. 

## Elasticsearch
For more detailed information about backup and restore of elasticsearch have a look at: 
[https://www.elastic.co/guide/en/elasticsearch/reference/7.17/snapshot-restore.html](https://www.elastic.co/guide/en/elasticsearch/reference/7.17/snapshot-restore.html)

### Configure backup directory
First you have to configure a backup directory:

#### Docker
If you are using a docker instance this has to be defined during creating container. e.g.:
To find the most recent version take a look at: [https://hub.docker.com/_/elasticsearch](https://hub.docker.com/_/elasticsearch)

```
docker run -d --name elastic4indexing  -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" -e "path.repo=/mnt/snapshot" -v "Path/to/local/snapshot/directory:/mnt/snapshot" elasticsearch:7.17.8
[...]
```
#### Local Installation
To configure backup directory you have to insert the following lines to
'/etc/elasticsearch/elasticsearch.yml':
``` 
#
# Path to snapshots:
#
path.repo: /absolute/path/to/snapshot/dir
```
--- 
NOTE
: 
- It's recommended to add these lines to the 'Paths' section.
- Please make sure that directory exists and is writable for service. (elasticsearch)

---
### Setup Directory for Snapshots
```
curl -X PUT "localhost:9200/_snapshot/snapshots?pretty" -H 'Content-Type: application/json' -d'
{
  "type": "fs",
  "settings": {
    "location": "backup_elastic",
    "readonly": false
  }
}'
```
Now there should be a subdirectory called 'backup_elastic' in the backup directory.
### Take a Single Snapshot
```
# curl -X PUT curl -X PUT "localhost:9200/_snapshot/snapshots/<snapshot_{now\d}>" 
# Due to url encoding this has to be writen as: 
curl -X PUT "localhost:9200/_snapshot/snapshots/%3Csnapshot_%7Bnow%2Fd%7D%3E"?pretty
{
  "accepted":true
}                                                           
$ more backup_elastic/index-0
{"snapshots":[{"name":"snapshot_2022.12.07","uuid":"zso5CWPUQqSey9o2C3Ul0g","state":1,"index_metadata_lookup":{},"version":"7.9.3"}],"indices":{},"min_version":"7.9.
0","index_metadata_identifiers":{}}
```
### Schedule Snapshots
In this example once a day at 1:00 a.m a snapshot should be made.
Max age of snapshot: 30d
Max number of snapshots: 50 

cron:  <seconds> <minutes> <hours> <day_of_month> <month> <day_of_week> [year]

```
curl -X PUT "localhost:9200/_slm/policy/always-snapshots?pretty" -H 'Content-Type: application/json' -d'
{
  "schedule": "0 0 1 * * ?",        
  "name": "<snapshot_{now/d}>",  
  "repository": "snapshots",        
  "config": {
    "indices": "*",
    "include_global_state": true
  },
  "retention": {
    "expire_after": "30d",
    "min_count": 5,
    "max_count": 50
  }
}
'
```

### List all available Snapshots
```
 curl -X GET "localhost:9200/_snapshot/snapshots/*" | jq .snapshots[].snapshot
# Alternatively if 'jq' is not installed:
curl -X GET "localhost:9200/_snapshot/snapshots/*"?pretty | grep \"snapshot\"
```
--- 
NOTE
: If you want to see the exact date and time of snapshot you may use **'\| jq .snapshots[].start_time,.snapshots[].snapshot'**

--- 

### Remove a Snapshot
```
curl -X DELETE "localhost:9200/_snapshot/snapshots/snapshot_2099.05.06?pretty"
{
  "acknowledged" : true
}
```
