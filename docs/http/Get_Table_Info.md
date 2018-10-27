---
layout: default
permalink: /docs/http/Get_Table_Info/
sidebar: yes
---

Get info on a Yamcs table:

    GET /api/archive/:instance/tables/:name

<div class="hint">
    This is low-level API for those cases where access to an internal key/value table of Yamcs is wanted. It is recommended to use other API operations for any of the default built-in tables.
</div>


### Response

<pre class="header">
Status: 200 OK
</pre>
```json
{
  "name" : "tm",
  "keyColumn" : [ {
    "name" : "gentime",
    "type" : "TIMESTAMP"
  }, {
    "name" : "seqNum",
    "type" : "INT"
  } ],
  "valueColumn" : [ {
    "name" : "rectime",
    "type" : "TIMESTAMP"
  }, {
    "name" : "packet",
    "type" : "BINARY"
  }, {
    "name" : "pname",
    "type" : "ENUM"
  } ]
}
```

### Alternative Media Types

#### Protobuf

Use HTTP header:

    Accept: application/protobuf
    
Response is of type:

<pre class="r header"><a href="{{ site.proto }}/archive/archive.proto">archive.proto</a></pre>
```proto
message TableInfo {
  optional string name = 1;
  repeated ColumnInfo keyColumn = 2;
  repeated ColumnInfo valueColumn = 3;
}
```
