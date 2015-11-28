---
layout: default
permalink: /docs/api/Edit_a_Link/
sidebar: yes
---

Edit a link:

    PATCH /api/links/:instance/:name


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
    <td>The state of the link. Either <tt>enabled</tt> or <tt>disabled</tt>.</td>
  </tr>
</table>

The same parameters can also be specified in the request body. In case both query string parameters and body parameters are specified, they are merged with priority being given to query string parameters.

### Example

Enable a link:

{% highlight json %}
{
  "state" : "enabled"
}
{% endhighlight %}

Disable a link:

{% highlight json %}
{
  "state" : "disabled"
}
{% endhighlight %}

### Protobuf

#### Request

<pre class="r header"><a href="/docs/api/rest.proto/">rest.proto</a></pre>
{% highlight proto %}
message PatchLinkRequest {
  optional string state = 1;
}
{% endhighlight %}
