---
layout: default
permalink: /docs/api/Edit_a_Client/
sidebar: yes
---

Edit a client:

    PATCH /api/clients/:id


### Parameters

<table class="inline">
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td class="code">processor</td>
    <td class="code">string</td>
    <td>The processor. This processor must be part of the instance that the client is connected to.</td>
  </tr>
  <tr>
    <td class="code">pretty</td>
    <td class="code">bool</td>
    <td>Format the JSON result in a human readable manner. Default: <tt>no</tt></td>
  </tr>
</table>

The same parameters can also be specified in the request body. In case both query string parameters and body parameters are specified, they are merged with priority being given to query string parameters.

### Example

Update the client's processor to <tt>replay123</tt>:

{% highlight json %}
{
  "processor" : "replay123"
}
{% endhighlight %}

### Protobuf

Request body is of type `Rest.PatchClientRequest`

{% highlight nginx %}
message PatchClientRequest {
  optional string processor = 1;
}
{% endhighlight %}
