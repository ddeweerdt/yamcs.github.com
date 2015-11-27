---
layout: default
permalink: /docs/api/List_Clients/
sidebar: yes
---

List all clients:

    GET /api/clients

List all clients for the given Yamcs instance:

    GET /api/instances/:instance/clients
    
List all clients for the given processor:

    GET /api/processors/:instance/:processor/clients 


### Response

<pre class="header">Status: 200 OK</pre>
{% highlight json %}
todo
{% endhighlight %}


### Protobuf

#### Response

<pre class="r header"><a href="/docs/api/rest.proto/">rest.proto</a></pre>
{% highlight proto %}
message ListClientsResponse {
  repeated yamcsManagement.ClientInfo client = 1;
}
{% endhighlight %}
