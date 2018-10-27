---
layout: default
permalink: /docs/http/Get_Tag/
sidebar: yes
---

Get info on a specific tag for the given archive instance:

    GET /api/archive/:instance/tags/:start/:id


### Response

<pre class="header">Status: 200 OK</pre>
```json
{
  "id" : 1,
  "name" : "My annotation",
  "start" : 1449128432000,
  "stop" : 1449174255000,
  "description" : "blabla",
  "color" : "#ffc800"
}
```

### Alternative Media Types

#### Protobuf

Use HTTP header:

    Accept: application/protobuf
    
Response is of type:

<pre class="r header"><a href="{{ site.proto }}/yamcs.proto">yamcs.proto</a></pre>
```proto
message ArchiveTag {
  optional int32 id = 1;
  required string name = 2;
  optional int64 start = 3;
  optional int64 stop = 4;
  optional string description = 5;
  optional string color = 6;
}
```
