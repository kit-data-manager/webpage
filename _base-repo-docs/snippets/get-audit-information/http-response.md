```http
HTTP/1.1 200 OK
Resource-Version: 4
Content-Type: application/vnd.datamanager.audit+json
Content-Length: 10815

[ {
  "changeType" : "ValueChange",
  "globalId" : {
    "entity" : "edu.kit.datamanager.repo.domain.DataResource",
    "cdoId" : "c9ddc646-e317-4d87-9ab8-a6be290e000d"
  },
  "commitMetadata" : {
    "author" : "SELF",
    "properties" : [ ],
    "commitDate" : "2022-02-24T09:45:21.645",
    "commitDateInstant" : "2022-02-24T08:45:21.645534100Z",
    "id" : 4.0
  },
  "property" : "publisher",
  "propertyChangeType" : "PROPERTY_VALUE_CHANGED",
  "left" : "SELF",
  "right" : "KIT Data Manager"
}, {
  "changeType" : "ValueChange",
  "globalId" : {
    "entity" : "edu.kit.datamanager.repo.domain.DataResource",
    "cdoId" : "c9ddc646-e317-4d87-9ab8-a6be290e000d"
  },
  "commitMetadata" : {
    "author" : "SELF",
    "properties" : [ ],
    "commitDate" : "2022-02-24T09:45:21.645",
    "commitDateInstant" : "2022-02-24T08:45:21.645534100Z",
    "id" : 4.0
  },
  "property" : "lastUpdate",
  "propertyChangeType" : "PROPERTY_VALUE_CHANGED",
  "left" : "2022-02-24T08:45:21.516Z",
  "right" : "2022-02-24T08:45:21.640Z"
}, {
  "changeType" : "SetChange",
  "globalId" : {
    "entity" : "edu.kit.datamanager.repo.domain.DataResource",
    "cdoId" : "c9ddc646-e317-4d87-9ab8-a6be290e000d"
  },
  "commitMetadata" : {
    "author" : "SELF",
    "properties" : [ ],
    "commitDate" : "2022-02-24T09:45:21.522",
    "commitDateInstant" : "2022-02-24T08:45:21.522533300Z",
    "id" : 3.0
  },
  "property" : "alternateIdentifiers",
  "propertyChangeType" : "PROPERTY_VALUE_CHANGED",
  "elementChanges" : [ {
    "elementChangeType" : "ValueAdded",
    "index" : null,
    "value" : {
      "entity" : "edu.kit.datamanager.entities.Identifier",
      "cdoId" : 2
    }
  } ]
}, {
  "changeType" : "ValueChange",
  "globalId" : {
    "entity" : "edu.kit.datamanager.repo.domain.DataResource",
    "cdoId" : "c9ddc646-e317-4d87-9ab8-a6be290e000d"
  },
  "commitMetadata" : {
    "author" : "SELF",
    "properties" : [ ],
    "commitDate" : "2022-02-24T09:45:21.522",
    "commitDateInstant" : "2022-02-24T08:45:21.522533300Z",
    "id" : 3.0
  },
  "property" : "lastUpdate",
  "propertyChangeType" : "PROPERTY_VALUE_CHANGED",
  "left" : "2022-02-24T08:45:21.361Z",
  "right" : "2022-02-24T08:45:21.516Z"
}, {
  "changeType" : "ValueChange",
  "globalId" : {
    "entity" : "edu.kit.datamanager.repo.domain.DataResource",
    "cdoId" : "c9ddc646-e317-4d87-9ab8-a6be290e000d"
  },
  "commitMetadata" : {
    "author" : "SELF",
    "properties" : [ ],
    "commitDate" : "2022-02-24T09:45:21.366",
    "commitDateInstant" : "2022-02-24T08:45:21.366532100Z",
    "id" : 2.0
  },
  "property" : "publicationYear",
  "propertyChangeType" : "PROPERTY_VALUE_CHANGED",
  "left" : "2022",
  "right" : "2017"
}, {
  "changeType" : "ValueChange",
  "globalId" : {
    "entity" : "edu.kit.datamanager.repo.domain.DataResource",
    "cdoId" : "c9ddc646-e317-4d87-9ab8-a6be290e000d"
  },
  "commitMetadata" : {
    "author" : "SELF",
    "properties" : [ ],
    "commitDate" : "2022-02-24T09:45:21.366",
    "commitDateInstant" : "2022-02-24T08:45:21.366532100Z",
    "id" : 2.0
  },
  "property" : "lastUpdate",
  "propertyChangeType" : "PROPERTY_VALUE_CHANGED",
  "left" : "2022-02-24T08:45:20.576Z",
  "right" : "2022-02-24T08:45:21.361Z"
}, {
  "changeType" : "NewObject",
  "globalId" : {
    "entity" : "edu.kit.datamanager.repo.domain.DataResource",
    "cdoId" : "c9ddc646-e317-4d87-9ab8-a6be290e000d"
  },
  "commitMetadata" : {
    "author" : "SELF",
    "properties" : [ ],
    "commitDate" : "2022-02-24T09:45:20.792",
    "commitDateInstant" : "2022-02-24T08:45:20.792498600Z",
    "id" : 1.0
  }
}, {
  "changeType" : "InitialValueChange",
  "globalId" : {
    "entity" : "edu.kit.datamanager.repo.domain.DataResource",
    "cdoId" : "c9ddc646-e317-4d87-9ab8-a6be290e000d"
  },
  "commitMetadata" : {
    "author" : "SELF",
    "properties" : [ ],
    "commitDate" : "2022-02-24T09:45:20.792",
    "commitDateInstant" : "2022-02-24T08:45:20.792498600Z",
    "id" : 1.0
  },
  "property" : "id",
  "propertyChangeType" : "PROPERTY_VALUE_CHANGED",
  "left" : null,
  "right" : "c9ddc646-e317-4d87-9ab8-a6be290e000d"
}, {
  "changeType" : "ReferenceChange",
  "globalId" : {
    "entity" : "edu.kit.datamanager.repo.domain.DataResource",
    "cdoId" : "c9ddc646-e317-4d87-9ab8-a6be290e000d"
  },
  "commitMetadata" : {
    "author" : "SELF",
    "properties" : [ ],
    "commitDate" : "2022-02-24T09:45:20.792",
    "commitDateInstant" : "2022-02-24T08:45:20.792498600Z",
    "id" : 1.0
  },
  "property" : "identifier",
  "propertyChangeType" : "PROPERTY_VALUE_CHANGED",
  "left" : null,
  "right" : {
    "entity" : "edu.kit.datamanager.repo.domain.PrimaryIdentifier",
    "cdoId" : 1
  }
}, {
  "changeType" : "SetChange",
  "globalId" : {
    "entity" : "edu.kit.datamanager.repo.domain.DataResource",
    "cdoId" : "c9ddc646-e317-4d87-9ab8-a6be290e000d"
  },
  "commitMetadata" : {
    "author" : "SELF",
    "properties" : [ ],
    "commitDate" : "2022-02-24T09:45:20.792",
    "commitDateInstant" : "2022-02-24T08:45:20.792498600Z",
    "id" : 1.0
  },
  "property" : "creators",
  "propertyChangeType" : "PROPERTY_VALUE_CHANGED",
  "elementChanges" : [ {
    "elementChangeType" : "ValueAdded",
    "index" : null,
    "value" : {
      "entity" : "edu.kit.datamanager.repo.domain.Agent",
      "cdoId" : 1
    }
  } ]
}, {
  "changeType" : "SetChange",
  "globalId" : {
    "entity" : "edu.kit.datamanager.repo.domain.DataResource",
    "cdoId" : "c9ddc646-e317-4d87-9ab8-a6be290e000d"
  },
  "commitMetadata" : {
    "author" : "SELF",
    "properties" : [ ],
    "commitDate" : "2022-02-24T09:45:20.792",
    "commitDateInstant" : "2022-02-24T08:45:20.792498600Z",
    "id" : 1.0
  },
  "property" : "titles",
  "propertyChangeType" : "PROPERTY_VALUE_CHANGED",
  "elementChanges" : [ {
    "elementChangeType" : "ValueAdded",
    "index" : null,
    "value" : {
      "entity" : "edu.kit.datamanager.repo.domain.Title",
      "cdoId" : 1
    }
  } ]
}, {
  "changeType" : "InitialValueChange",
  "globalId" : {
    "entity" : "edu.kit.datamanager.repo.domain.DataResource",
    "cdoId" : "c9ddc646-e317-4d87-9ab8-a6be290e000d"
  },
  "commitMetadata" : {
    "author" : "SELF",
    "properties" : [ ],
    "commitDate" : "2022-02-24T09:45:20.792",
    "commitDateInstant" : "2022-02-24T08:45:20.792498600Z",
    "id" : 1.0
  },
  "property" : "publisher",
  "propertyChangeType" : "PROPERTY_VALUE_CHANGED",
  "left" : null,
  "right" : "SELF"
}, {
  "changeType" : "InitialValueChange",
  "globalId" : {
    "entity" : "edu.kit.datamanager.repo.domain.DataResource",
    "cdoId" : "c9ddc646-e317-4d87-9ab8-a6be290e000d"
  },
  "commitMetadata" : {
    "author" : "SELF",
    "properties" : [ ],
    "commitDate" : "2022-02-24T09:45:20.792",
    "commitDateInstant" : "2022-02-24T08:45:20.792498600Z",
    "id" : 1.0
  },
  "property" : "publicationYear",
  "propertyChangeType" : "PROPERTY_VALUE_CHANGED",
  "left" : null,
  "right" : "2022"
}, {
  "changeType" : "ReferenceChange",
  "globalId" : {
    "entity" : "edu.kit.datamanager.repo.domain.DataResource",
    "cdoId" : "c9ddc646-e317-4d87-9ab8-a6be290e000d"
  },
  "commitMetadata" : {
    "author" : "SELF",
    "properties" : [ ],
    "commitDate" : "2022-02-24T09:45:20.792",
    "commitDateInstant" : "2022-02-24T08:45:20.792498600Z",
    "id" : 1.0
  },
  "property" : "resourceType",
  "propertyChangeType" : "PROPERTY_VALUE_CHANGED",
  "left" : null,
  "right" : {
    "entity" : "edu.kit.datamanager.repo.domain.ResourceType",
    "cdoId" : 1
  }
}, {
  "changeType" : "SetChange",
  "globalId" : {
    "entity" : "edu.kit.datamanager.repo.domain.DataResource",
    "cdoId" : "c9ddc646-e317-4d87-9ab8-a6be290e000d"
  },
  "commitMetadata" : {
    "author" : "SELF",
    "properties" : [ ],
    "commitDate" : "2022-02-24T09:45:20.792",
    "commitDateInstant" : "2022-02-24T08:45:20.792498600Z",
    "id" : 1.0
  },
  "property" : "dates",
  "propertyChangeType" : "PROPERTY_VALUE_CHANGED",
  "elementChanges" : [ {
    "elementChangeType" : "ValueAdded",
    "index" : null,
    "value" : {
      "entity" : "edu.kit.datamanager.repo.domain.Date",
      "cdoId" : 1
    }
  } ]
}, {
  "changeType" : "SetChange",
  "globalId" : {
    "entity" : "edu.kit.datamanager.repo.domain.DataResource",
    "cdoId" : "c9ddc646-e317-4d87-9ab8-a6be290e000d"
  },
  "commitMetadata" : {
    "author" : "SELF",
    "properties" : [ ],
    "commitDate" : "2022-02-24T09:45:20.792",
    "commitDateInstant" : "2022-02-24T08:45:20.792498600Z",
    "id" : 1.0
  },
  "property" : "alternateIdentifiers",
  "propertyChangeType" : "PROPERTY_VALUE_CHANGED",
  "elementChanges" : [ {
    "elementChangeType" : "ValueAdded",
    "index" : null,
    "value" : {
      "entity" : "edu.kit.datamanager.entities.Identifier",
      "cdoId" : 1
    }
  } ]
}, {
  "changeType" : "InitialValueChange",
  "globalId" : {
    "entity" : "edu.kit.datamanager.repo.domain.DataResource",
    "cdoId" : "c9ddc646-e317-4d87-9ab8-a6be290e000d"
  },
  "commitMetadata" : {
    "author" : "SELF",
    "properties" : [ ],
    "commitDate" : "2022-02-24T09:45:20.792",
    "commitDateInstant" : "2022-02-24T08:45:20.792498600Z",
    "id" : 1.0
  },
  "property" : "lastUpdate",
  "propertyChangeType" : "PROPERTY_VALUE_CHANGED",
  "left" : null,
  "right" : "2022-02-24T08:45:20.576Z"
}, {
  "changeType" : "InitialValueChange",
  "globalId" : {
    "entity" : "edu.kit.datamanager.repo.domain.DataResource",
    "cdoId" : "c9ddc646-e317-4d87-9ab8-a6be290e000d"
  },
  "commitMetadata" : {
    "author" : "SELF",
    "properties" : [ ],
    "commitDate" : "2022-02-24T09:45:20.792",
    "commitDateInstant" : "2022-02-24T08:45:20.792498600Z",
    "id" : 1.0
  },
  "property" : "state",
  "propertyChangeType" : "PROPERTY_VALUE_CHANGED",
  "left" : null,
  "right" : "VOLATILE"
}, {
  "changeType" : "SetChange",
  "globalId" : {
    "entity" : "edu.kit.datamanager.repo.domain.DataResource",
    "cdoId" : "c9ddc646-e317-4d87-9ab8-a6be290e000d"
  },
  "commitMetadata" : {
    "author" : "SELF",
    "properties" : [ ],
    "commitDate" : "2022-02-24T09:45:20.792",
    "commitDateInstant" : "2022-02-24T08:45:20.792498600Z",
    "id" : 1.0
  },
  "property" : "acls",
  "propertyChangeType" : "PROPERTY_VALUE_CHANGED",
  "elementChanges" : [ {
    "elementChangeType" : "ValueAdded",
    "index" : null,
    "value" : {
      "entity" : "edu.kit.datamanager.repo.domain.acl.AclEntry",
      "cdoId" : 1
    }
  } ]
} ]
```