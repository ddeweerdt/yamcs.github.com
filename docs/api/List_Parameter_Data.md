---
layout: default
permalink: /docs/api/List_Parameter_Data/
sidebar: yes
---

List the history of values for the specified parameter:

    GET /api/archive/:instance/parameters/:namespace/:name


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
        <td class="code">norepeat</td>
        <td class="code">bool</td>
        <td>Whether to filter out consecutive identical values. Default <tt>no</tt>.</td>
    </tr>
    <tr>
        <td class="code">pos</td>
        <td class="code">integer</td>
        <td>The zero-based row number at which to start outputting results. Default: <tt>0</tt></td>
    </tr>
    <tr>
        <td class="code">limit</td>
        <td class="code">integer</td>
        <td>The maximum number of returned records per page. Choose this value too high and you risk hitting the maximum response size limit enforced by the server. Default: <tt>100</tt></td>
    </tr>
    <tr>
        <td class="code">order</td>
        <td class="code">string</td>
        <td>The order of the returned results. Can be either <tt>asc</tt> or <tt>desc</tt>. Default: <tt>desc</tt></td>
    </tr>
</table>

The <tt>pos</tt> and <tt>limit</tt> allow for pagination. Keep in mind that in-between two requests extra data may have been recorded, causing a shift of the results. This generic stateless operation does not provide a reliable mechanism against that, so address it by overlapping your <tt>pos</tt> parameter with rows of the previous query. In this example we overlap by 4:

    ?pos=0&limit=50&order=desc
    ?pos=45&limit=50&order=desc 


### Response

<pre class="header">
Status: 200 OK
</pre>

{% highlight json %}
{
  "parameter" : [ {
    "id" : {
      "name" : "BatteryVoltage2",
      "namespace" : "/YSS/SIMULATOR"
    },
    "rawValue" : {
      "type" : "UINT32",
      "uint32Value" : 144
    },
    "engValue" : {
      "type" : "UINT32",
      "uint32Value" : 144
    },
    "acquisitionTime" : 1447417449218,
    "generationTime" : 1447417432121,
    "acquisitionStatus" : "ACQUIRED",
    "processingStatus" : true,
    "monitoringResult" : "IN_LIMITS",
    "acquisitionTimeUTC" : "2015-11-13T12:23:33.218",
    "generationTimeUTC" : "2015-11-13T12:23:16.121",
    "expirationTime" : 1447417456218,
    "expirationTimeUTC" : "2015-11-13T12:23:40.218",
    "alarmRange" : [ {
      "level" : "WATCH",
      "minInclusive" : 50.0
    }, {
      "level" : "WARNING",
      "minInclusive" : 40.0
    }, {
      "level" : "DISTRESS",
      "minInclusive" : 30.0
    }, {
      "level" : "CRITICAL",
      "minInclusive" : 20.0
    }, {
      "level" : "SEVERE",
      "minInclusive" : 10.0
    } ]
  } ]
}
{% endhighlight %}

### Alternative Media Types

#### CSV

Use HTTP header:

    Accept: text/csv

Or, add this query parameter: `format=csv`.

<pre class="header">
Status: 200 OK
Content-Type: text/csv
</pre>

{% highlight text %}
Time    BatteryVoltage2
2015-11-13T12:21:55.199 157
2015-11-13T12:21:48.972 158
2015-11-13T12:21:42.750 159                       
{% endhighlight %}


#### Protobuf

Use HTTP header:

    Accept: application/protobuf

Response if of type:

<pre class="r header"><a href="/docs/api/pvalue.proto/">pvalue.proto</a></pre>
{% highlight proto %}
message ParameterData {
  repeated ParameterValue parameter = 1;
}
{% endhighlight %}
