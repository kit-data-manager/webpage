---
title:  Ingest a Metadata Document
breadcrumbs: /metastore/documentation/frontend
layout: default
description: A Research Data Repository Service for Managing Metadata Documents based on JSON or XML.
repository_url: https://github.com/kit-data-manager/metastore2
repository_name: kit-data-manager/metastore2
navigation_id: metastore_doc
---

# {{ page.title }} 
MetaStore will not provide plain text files. As only JSON and XML are supported 
the metadata documents have to fulfill a given (JSON/XML) schema.
The GUI has full support of JSON and XML documents. 
## Ingredients

- (local) MetaStore instance
- Web Browser
- Already registered schema ([see 'Schema Management'](../schema/introduction.html))
- Data related to the metadata

---

## Work Steps (Summary)

### Ingest a metadata document
 * Step 1: Check if schema is already registered?
 * Step 2: Select registered schema
 * Step 3: Create metadata document

---

## Step 1: Check if schema is already registered?
If the schema your metadata document should use is not already registered please have a look at chapter ['Select/create a Schema'](../schema/select.html). 


## Step 2: Select registered schema
Note the 'Schema Record Identifier' of selected schema.

## Step3: Create metadata document
Fortunately the GUI of MetaStore supports users to input metadata document. 
1. Select tab 'Metadata Management'
2. Click on 'Register new metadata document'
3. Fill form like seen below


<div class="centerbox">
    <img src="../images/MetadataListing.png" alt="Metadata Management Table" style="max-height:50em;" />
</div>

***Notes:*** 
- If no authentication is made, all users are registered as 'SELF'. Otherwise 
the one who registers the schema gets the administration rights. 
- Identifier is optional and if given it has to be unique. (If no identifier is 
specified it will be set to a UUID.)
- It's recommended to use a URL as identifier for the related resource.
- Select previously noted 'Schema Record Identifier' as schema identifier.

The record may be filled like this:
<div class="centerbox">
    <img src="../images/MetadataRecord.png" alt="Input Form for metadata document" style="max-height:50em;" />
</div>

Click on 'Validate' to check the provided settings.
If validation was successful the tab header will be greened:
<div class="centerbox">
    <img src="../images/MetadataRecord2.png" alt="Input Form for metadata document" style="max-height:50em;" />
</div>

Now you can switch to 'Metadata Document' tab to insert metadata document from scratch (if not uploaded a file in beforehand). The editor look like this (blank document):

<div class="centerbox">
    <img src="../images/MetadataEditor.png" alt="Input Form for metadata document" style="max-height:50em;" />
</div>

As you can see the editor supports autocompletion and supports you with information about the fields. Press 'space' or '"' to 
get support about...

...possible entries...
<div class="centerbox">
    <img src="../images/MetadataEditor2.png" alt="List of Metadata Documents" style="max-height:50em;" />
</div>
...format of author field...
<div class="centerbox">
    <img src="../images/MetadataEditor3.png" alt="List of Metadata Documents" style="max-height:50em;" />
</div>
...format of date field...
<div class="centerbox">
    <img src="../images/MetadataEditor4.png" alt="List of Metadata Documents" style="max-height:50em;" />
</div>
...format of title.
<div class="centerbox">
    <img src="../images/MetadataEditor5.png" alt="List of Metadata Documents" style="max-height:50em;" />
</div>

After you have finished your document you click on 'Submit'


<div class="centerbox">
    <img src="../images/MetadataListing2.png" alt="List of Metadata Documents" style="max-height:50em;" />
</div>

***Congratulations, you successfully registered your first metadata document!***


<style>
td, th {
   border: none!important;
}
</style>
| [<< PREVIOUS](introduction.html)|[NEXT >>](read.html)|
|:----|----:|
| | |
