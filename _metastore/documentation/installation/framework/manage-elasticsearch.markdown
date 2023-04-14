---
title:  Manage Elasticsearch Instance
breadcrumbs: /metastore/documentation/installation/framework/Manage Elastic
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_instal
---

# {{ page.title }} 

## Customize Mapping for Index
If there occur some errors during mapping it might be neccessary to customize the mapping for a specific index.
### Take a Snapshot
[Take a Single Snapshot](backup-metastore.html#take-a-single-snapshot) as described below.
### Save Current Mapping of Index

```
curl -X GET http://localhost:9200/YOUR_INDEX/_mapping?pretty > YOUR_INDEX_mapping.json

```
### Clear Index
```
curl -X DELETE http://localhost:9200/YOUR_INDEX
```
### Customize Saved Mapping to Your Needs
Unfortunately you have to remove the top level element (should be 'YOUR_INDEX') from the file.
Example: 
```
YOUR_INDEX_mapping.json:
{
 "YOUR_INDEX" : {
   "mappings" : {
     [...]
   }
 }
}
--> 
mapping.json:
{
  "mappings" : {
    [...]
  }
}
```
Save new file as 'mapping.json'.
If you have 'jq' installed this can be easily done with 
```
cat YOUR_INDEX_mapping.json | jq .YOUR_INDEX > mapping.json
```
### Push Mapping for Index
```
curl -X PUT  http://localhost:9200/YOUR_INDEX -H 'Content-Type: application/json' --data '@mapping.json'
```
### Reindex all Entries of 'YOUR_INDEX'
```
systemctl stop metaStore 
bash run.sh --reindex --indices YOUR_INDEX
[...]
```
Reindexing may take a while depending on the number of entries.
(As the script runs not in background you should interrupt the script afte indexing has finished and start the daemon again. 


<style>
td, th {
   border: none!important;
}
</style>
|  [<< PREVIOUS](setup-elasticsearch.html)|[NEXT >>](setup-rabbitMq.html)|
|:----|----:|
| | |
