---
title: Implementation
breadcrumbs: /collection-registry/documentation/
layout: default
description: A General Purpose Service for building Research Data Collections.
repository_url: https://github.com/kit-data-manager/collection-api
repository_name: kit-data-manager/collection-api
navigation_id: collection_registry_index
---

# Implementation

In this section, implementation details are described. You'll find a description of the collection data model as well as overall service architecture.


## Service Architecture

The architecture of the Collection Registry is illustrated in the figure below. The bottom component is the Collection API core, which 
includes the collection implementation. The service contains various REST APIs responsible for interacting with users and thus enabling 
collections and collection items management. Moreover, the service offers a graphical web frontend in order to visualize managed collections, 
collection items and relationships between them. The web frontend is available under http://{hostname}:{port}/static/overview.html. 

<img src='/webpage/assets/images/collection-registry/architecture.png'/>
Figure 1: Collection Registry architecture

## Supported Service Features

The table below includes the different service-level features this implementation offers. Those features depend on the implementation itself and 
cannot be changed externally.

| feature                       | description                                                      | supported
|-------------------------------|------------------------------------------------------------------|----
| providesCollectionPids        | The service can create PIDs for collections and member items.    | No, should be handled externally.
| collectionPidProviderType     | Supported PID providers.                                         | No, should be handled externally.
| enforcesAccess                | Service enforces access control checks on collection access.     | No
| supportsPagination            | Collections can be listed page-wise.                             | Yes
| asynchronousActions           | Asynchronous actions, e.g., on update, are supported.            | No
| ruleBasedGeneration           | Collections can be automatically created based on certain rules. | No
| maxExpansionDepth             | The maximum expand depth of collections while listing.           | true (infinite)
| providesVersioning            | Versioning of collections and their member items is supported.   | No
| supportedCollectionOperations | Machine-actionable operations are supported for collections.     | No
| supportedModelTypes           | List of supported model types offered by this service.           | No limitation.

## Data Model

The Collection Registry offers the possibility to create and manage collections and collection items. 
The figure below includes a data model of a collection, collection item and the relationship between them.

<img src='/webpage/assets/images/collection-registry/collectionDataModel.png'/>
Figure 2: Collections and collection items

Each collection holds the following attributes: 

| attribute    | description                                                  
|--------------|----------------------------------------------------------------------------------
| id           | The identifier of the collection, e.g., internal or PID.
| description  | Descriptive metadata for the collection, which may have to comply to an ontology.
| capabilities | Supported collection capabilities (see below). 
| properties   | A set of collection properties (see below).

### Collection Capabilities

Collection capabilities define, what can be done with a certain collection and how it behaves under certain circumstances.
The following table shows supported capabilities, their description and defaults. 

| attribute            | description                                                                                                                                                | default
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------
| isOrdered            | Determines, if a collection is kept in a defined order. The Collection Registry supports manual ordering by index (see 'Collection Item Mapping Metadata') | false
| appendsToEnd         | State that new elements are appended to the end. Only valid for ordered collections.                                                                       | true 
| supportsRoles        | Indicates whether the collection supports assigning roles to its member items.                                                                             | false                                    
| membershipIsMutable  | Indicates whether collection membership are mutable (i.e. whether items can be added and removed)                                                          | true 
| propertiesAreMutable | Indicates whether collection properties are mutable (i.e. can the metadata of this collection be changed)                                                  | true
| restrictedToType     | If specified, indicates that the collection is made up of homogenous items of the specified type.                                                          | null
| maxLength            | The maximum length of the Collection. -1 means length is not restricted.                                                                                   | -1

### Collection Properties

| attribute             | description                                                                                                                                                    | default
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------
| dateCreated           | The date when the collection has been created.                                                                                                                 | The creation date
| ownership             | Indicates the owner of the Collection. Implementation is expected to use a controlled vocabulary or PIDs.                                                      | null
| license               | Indicates the license that applies to the Collection. Implementation is expected to use a controlled vocabulary, stable URIs or PIDs of registered data types. | null
| modelType             | Identifies the model that the collection adheres to. Iimplementation is expected to use a controlled vocabulary, or PIDs of registered data types.             | null
| hasAccessRestrictions | Indicates whether the collection is fully open or has access restrictions.                                                                                     | false
| memberOf              | If provided, this is a list of collection identifiers to which this collection itself belongs.                                                                 | [] (empty list)
| descriptionOntology   | Identifies the ontology used for descriptive metadata. Implementation is expected to supply the URI of a controlled vocabulary.                                | null
| smartRules   | A list of rules applied to added members for deciding, whether the member is added to this collection (no rule applies) or to one more more other collections as defined by the rule which applies.                                | null

#### Rule-based Collections

Introduced in version 1.3.0, the Collection Registry supports rule-based collections. Rules are defined in the collection properties by string. Each rule consists of four parts:

- The field which is checked
- The comparator which is applies
- The comparator term the field should match
- The target collection id a member is added to if the rules applies

Together with some delimiters and separators for better parsing, a valid rule looks like:

```
DATA_TYPE EQUALS 'application/json' > json-metadata
```

Which means, "put all members whose *dataType* field value *equals* the string *application/json* to collection *json-metadata*.
If collection *json-metadata* does not exist, yet, it will be created as sub-collection of the collection the addMember operation was applied to. If the collection already exists, either as member of the target collection or not, the new member will be added.

---
**NOTE**
Restrictions, e.g., by collection capabilities and properties, are only checked for the collection the addMember operation was applied to. If a smart-rules applied to a member, for the new target collection NO further checks are applied. E.g., a collection might be filled beyond its maxLength by a smart rule.

---

If none of the provided rules apply, the member will be added to the collection the addMember operation was applied to.

The following values are supported for the certain parts:

**Field:**

| Value             | Target field
|-------------------|-----------
| MEMBER_ID         | mid  
| DATA_TYPE         | datatype 
| DESCRIPTION       | description
| LOCATION          | location
| ONTOLOGY          | ontology
| MEMBER_ROLE       | mappings.memberRole

(For field descriptions see table in next chapter)

**Operator:**

| Value             | Notes
|-------------------|-----------
| STARTS_WITH       | -
| ENDS_WITH         | -
| CONTAINS          | -
| NOT_CONTAINS      | -
| EQUALS            | Case-sensitive equals 
| NOT_EQUALS        | -
| EQUALS_IGNORE_CASE| Case-insensive equals
| MATCHES           | Regular expression
        
The following table shows some example rules with a short description on what they mean:

| Rule              | Description
|-------------------|-----------
| DATA_TYPE STARTS_WITH 'image' > images   | Put all members with a dataType starting with *image* to a collection with id *images*.
| LOCATION CONTAINS 'localhost' > local_members  | Put all members with a location containing *localhost* to a collection with id *local_members*
| DESCRIPTION NOT_CONTAINS 'pre-release' > released | Put all members not containing 'pre-release' in their description to a collection with id *released*


### Collection Item Properties

Each collection item holds the following attributes:

| attribute    | description
|--------------|----------------------------------------------------------------------------------
| id           | The identifier of the collection item, e.g., internal or PID.
| mid          | The id of the parent collection (will be assigned by the service automatically)
| location  | The location (URL) the item refers to.
| description    | A human readable description of the member item.
| datatype     | Data type of the item, which is needed, if the parent is `restrictedToType`.
| ontology     | URI of an ontology model class that applies to this item.
| mappings     | Metadata related to the parent collection (see below).


### Collection Item Mapping Metadata

| attribute         | description
|-------------------|------------------------------------------------------------------------------------------------------------
| memberRole        | The role that applies to this item. Only available if the collection supportsRoles per its capabilities.
| index             | Position of the item in the collection. Only available if the Collection `isOrdered` per its capabilities.
| dateAdded         | The date the item was added to the collection.
| dateUpdated       | The date the item's metadata were last updated.

