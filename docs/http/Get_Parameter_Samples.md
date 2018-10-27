---
layout: default
permalink: /docs/http/Get_Parameter_Samples/
sidebar: yes
---

Sample the history of values for the specified parameter:

    GET /api/archive/:instance/parameters/:namespace/:name/samples   

<div class="hint">
    By default this operation fetches data from the parameter archive and/or parameter cache. If these services are not configured, you can still get correct results by specifying the option <tt>source=replay</tt> as detailed below.
</div>


### Parameters

<table class="inline">
    <tr>
        <th>Name</th>
        <th>Type</th>
        <th>Description</th>
    </tr>
    <tr>
        <td class="code">start</td>
        <td class="code">string</td>
        <td>Filter the lower bound of the parameter's generation time. Specify a date string in ISO 8601 format</td>
    </tr>
    <tr>
        <td class="code">stop</td>
        <td class="code">string</td>
        <td>Filter the upper bound of the parameter's generation time. Specify a date string in ISO 8601 format</td>
    </tr>
    <tr>
        <td class="code">count</td>
        <td class="code">int</td>
        <td>Number of returned samples. Default: <tt>500</tt></td>
    </tr>
    <tr>
        <td class="code">order</td>
        <td class="code">string</td>
        <td>The order of the returned results. Can be either <tt>asc</tt> or <tt>desc</tt>. Default: <tt>asc</tt></td>
    </tr>
    <tr>
        <td class="code">norealtime</td>
        <td class="code">boolean</td>
        <td>Disable loading of parameters from the parameter cache. Default: <tt>false</tt></td>
    </tr>
    <tr>
        <td class="code">processor</td>
        <td class="code">string</td>
        <td>The name of the processor from which to use the parameter cache. Default: <tt>realtime</tt></td>
    </tr>
    <tr>
        <td class="code">source</td>
        <td class="code">string</td>
        <td>Specifies how to retrieve the parameters. Either <tt>ParameterArchive</tt> or <tt>replay</tt>. If <tt>replay</tt> is specified, a replay processor will be created and data will be processed with the active XTCEDB. Note that this is much slower than receiving data from the ParameterArchive.<br>Default: <tt>ParameterArchive</tt></td>
    </tr>
</table>
 

### Response

<pre class="header">Status: 200 OK</pre>
```json
{
  "sample" : [ {
    "time" : "2015-11-11T09:11:37.626",
    "avg" : 169.41836734693865,
    "min" : 103.0,
    "max" : 237.0,
    "n" : 98
  } ]
}
```

### Alternative Media Types

#### Protobuf

Use HTTP header:

    Accept: application/protobuf
    
Response is of type:

<pre class="r header"><a href="{{ site.proto }}/pvalue/pvalue.proto">pvalue.proto</a></pre>
```proto
message TimeSeries {
  message Sample {
    optional string time = 1;
    optional double avg = 2;
    optional double min = 3;
    optional double max = 4;
    optional int32 n = 5;
  }

  repeated Sample sample = 1;
}
```
