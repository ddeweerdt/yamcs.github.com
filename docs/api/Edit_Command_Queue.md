---
layout: default
permalink: /docs/api/Edit_Command_Queue/
sidebar: yes
---

Edit a command queue:

    PATCH /api/processors/:instance/:processor/cqueues/:name


### Parameters

<table class="inline">
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td class="code">state</td>
    <td class="code">string</td>
    <td>The state of the queue. Either <tt>enabled</tt>, <tt>disabled</tt> or <tt>blocked</tt>.</td>
  </tr>
</table>

The same parameters can also be specified in the request body. In case both query string parameters and body parameters are specified, they are merged with priority being given to query string parameters.

### Example

Block a queue:

{% highlight json %}
{
  "state" : "blocked"
}
{% endhighlight %}

The response contains the updated queue information:

<pre class="header">Status: 200 OK</pre>
{% highlight json %}
{
  "instance" : "simulator",
  "processorName" : "realtime",
  "name" : "default",
  "state" : "BLOCKED",
  "nbSentCommands" : 0,
  "nbRejectedCommands" : 0,
  "url" : "http://localhost:8090/api/processors/simulator/realtime/cqueues/default"
}
{% endhighlight %}

### Alternative Media Types

#### Protobuf

Use these HTTP headers:

    Content-Type: application/protobuf
    Accept: application/protobuf
    
Request is of type:

<pre class="r header"><a href="/docs/api/rest.proto/">rest.proto</a></pre>
{% highlight proto %}
message EditCommandQueueRequest {
  optional string state = 1;
}
{% endhighlight %}

Response is of type:

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
  repeated CommandQueueEntry entry = 8;
  optional string url = 9;
}
{% endhighlight %}
