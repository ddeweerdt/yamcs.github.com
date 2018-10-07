---
layout: default
permalink: /docs/http/List_Links/
sidebar: yes
---

List all links:

    GET /api/links

List all links for the given Yamcs instance:

    GET /api/links/:instance 


### Response

<pre class="header">Status: 200 OK</pre>
```json
{
  "link" : [ {
    "instance" : "simulator",
    "name" : "tm1",
    "type" : "HkDataHandler",
    "spec" : "",
    "stream" : "tm_realtime",
    "disabled" : false,
    "status" : "OK",
    "dataCount" : 34598,
    "detailedStatus" : "reading files from /storage/yamcs-incoming/simulator/tm"
  } ]
}
```


### Alternative Media Types

#### Protobuf

Use HTTP header:

    Accept: application/protobuf
    
Response is of type:

<pre class="r header"><a href="/docs/http/rest.proto/">rest.proto</a></pre>
```proto
message ListLinkInfoResponse {
  repeated yamcsManagement.LinkInfo link = 1;
}
```
