---
layout: default
permalink: /docs/api/Get_Command_Queue/
sidebar: yes
---

Get data on a command queue:

    GET /api/processors/:instance/:processor/cqueues/:name


### Response

{% highlight json %}
{
  "instance" : "simulator",
  "processorName" : "realtime",
  "name" : "default",
  "state" : "BLOCKED",
  "nbSentCommands" : 0,
  "nbRejectedCommands" : 0,
  "entry" : [ {
    "instance" : "simulator",
    "processorName" : "realtime",
    "queueName" : "default",
    "cmdId" : {
      "generationTime" : 1448782973440,
      "origin" : "000349-WS.local",
      "sequenceNumber" : 5,
      "commandName" : "/YSS/SIMULATOR/SWITCH_VOLTAGE_OFF"
    },
    "source" : "SWITCH_VOLTAGE_OFF(voltage_num: 2)",
    "binary" : "GGTAAAAAAAAAAABqAAAAAgI=",
    "username" : "anonymous",
    "generationTime" : 1448782973440,
    "uuid" : "3e867111-048a-4343-b195-47ba07d07093"
  } ],
  "url" : "http://localhost:8090/api/processors/simulator/realtime/cqueues/default"
}
{% endhighlight %}

### Protobuf

#### Response

<pre class="r header"><a href="/docs/api/commanding.proto/">commanding.proto</a></pre>
{% highlight proto %}
message CommandQueueInfo {
  required string instance = 1;
  required string processorName = 2;
  required string name = 3;
  optional QueueState state = 4;
  required int32 nbSentCommands = 5;
  required int32 nbRejectedCommands = 6;
  optional int32 stateExpirationTimeS = 7;
  optional string url = 8;
}
{% endhighlight %}
