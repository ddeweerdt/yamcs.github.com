---
layout: default
permalink: /docs/api/Get_MDB_Detail/
sidebar: yes
---

Get data on a the Mission Database for the given Yamcs instance:

    GET /api/mdb/:instance


### Response

<pre class="header">Status: 200 OK</pre>
{% highlight json %}
{
  "configName" : "landing",
  "name" : "",
  "spaceSystem" : [ {
    "name" : "YSS",
    "qualifiedName" : "/YSS",
    "version" : "1.2",
    "parameterCount" : 3,
    "containerCount" : 1,
    "commandCount" : 1,
    "sub" : [ {
      "name" : "SIMULATOR",
      "qualifiedName" : "/YSS/SIMULATOR",
      "version" : "1.0",
      "parameterCount" : 59,
      "containerCount" : 9,
      "commandCount" : 8,
      "history" : [ {
        "version" : "1.3",
        "date" : "21-June-2020",
        "message" : "modified this and that"
      } ]
    } ]
}
{% endhighlight %}

### Protobuf

Response:

<pre class="r header"><a href="/docs/api/yamcsManagement.proto/">yamcsManagement.proto</a></pre>
{% highlight proto %}
message MissionDatabase {
  required string configName = 1;
  required string name = 2;
  optional string version = 3;
  repeated SpaceSystemInfo spaceSystem = 4;
  optional string url = 5;
  optional string parametersUrl = 6;
  optional string containersUrl = 7;
  optional string commandsUrl = 8;
}
{% endhighlight %}
