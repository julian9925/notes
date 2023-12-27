---
id: 3793y7n35v2sjshzrvje4ye
title: redfish intro
desc: ''
updated: 1700642400473
created: 1700451111052
---

## Data Model

### Resource
  A Resource is defined as a single entity. Each resource is strongly typed and defined in a Redfish schema document, identifiable in the response payload by a unique type identifier property.

  The response for a single resource typically contains properties like:
  
 - @odata.id
 - @odata.type
 - Id
 - Name

  Responses may also contain other properties defined within the schema for that resource type.

### Resource Collections
  A Resource Collection is a collection of resources share the same schema definition.

  Responses for Resource Collections may contain the following properties:
 - @odata.context
 - @odata.etag
 - Description
 - Members
 - @odata.nextLink
 - Oem

