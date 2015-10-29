---
layout: default
permalink: /docs/api/List_Active_Alarms/
sidebar: yes
---

Returns a list of current active alarms. For each alarm you get full information on the value occurrence that initially triggered the alarm, the most severe value since it originally triggered, and the latest value at the time of your request.

    GET /api/processors/:instance/:processor/alarms


### Parameters

<table class="inline">
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td class="code">pretty</td>
    <td class="code">bool</td>
    <td>Format the JSON result in a human readable manner. Default: <tt>no</tt></td>
  </tr>
</table>

### Response

When using Protobuf, the response can be deserialized as `Rest.GetAlarmsResponse`.

Protobuf definition:

{% highlight nginx %}
message GetAlarmsResponse {
   repeated alarms.Alarm alarms = 1;
}
{% endhighlight %}

### Example

```
curl -XGET http://localhost:8090/simulator/api/alarms?pretty
```
{% highlight json %}
{
  "alarms" : [ {
    "id" : 3,
    "triggerValue" : {
      "id" : {
        "name" : "/YSS/SIMULATOR/O2TankTemp"
      },
      "rawValue" : {
        "type" : 2,
        "uint32Value" : 227
      },
      "engValue" : {
        "type" : 2,
        "uint32Value" : 227
      },
      "acquisitionTime" : 1440576556724,
      "generationTime" : 1440576539714,
      "acquisitionStatus" : 0,
      "processingStatus" : true,
      "monitoringResult" : 21,
      "acquisitionTimeUTC" : "2015-08-26T08:08:40.724",
      "generationTimeUTC" : "2015-08-26T08:08:23.714",
      "watchLow" : 10.0,
      "watchHigh" : 12.0,
      "warningLow" : 30.0,
      "warningHigh" : 32.0,
      "distressLow" : 40.0,
      "distressHigh" : 42.0,
      "criticalLow" : 60.0,
      "criticalHigh" : 62.0,
      "severeLow" : 80.0,
      "severeHigh" : 82.0,
      "expirationTime" : 1440576558224,
      "expirationTimeUTC" : "2015-08-26T08:08:42.224"
    },
    "mostSevereValue" : {
      "id" : {
        "name" : "/YSS/SIMULATOR/O2TankTemp"
      },
      "rawValue" : {
        "type" : 2,
        "uint32Value" : 227
      },
      "engValue" : {
        "type" : 2,
        "uint32Value" : 227
      },
      "acquisitionTime" : 1440576556724,
      "generationTime" : 1440576539714,
      "acquisitionStatus" : 0,
      "processingStatus" : true,
      "monitoringResult" : 21,
      "acquisitionTimeUTC" : "2015-08-26T08:08:40.724",
      "generationTimeUTC" : "2015-08-26T08:08:23.714",
      "watchLow" : 10.0,
      "watchHigh" : 12.0,
      "warningLow" : 30.0,
      "warningHigh" : 32.0,
      "distressLow" : 40.0,
      "distressHigh" : 42.0,
      "criticalLow" : 60.0,
      "criticalHigh" : 62.0,
      "severeLow" : 80.0,
      "severeHigh" : 82.0,
      "expirationTime" : 1440576558224,
      "expirationTimeUTC" : "2015-08-26T08:08:42.224"
    },
    "currentValue" : {
      "id" : {
        "name" : "/YSS/SIMULATOR/O2TankTemp"
      },
      "rawValue" : {
        "type" : 2,
        "uint32Value" : 223
      },
      "engValue" : {
        "type" : 2,
        "uint32Value" : 223
      },
      "acquisitionTime" : 1440577186414,
      "generationTime" : 1440577169410,
      "acquisitionStatus" : 0,
      "processingStatus" : true,
      "monitoringResult" : 21,
      "acquisitionTimeUTC" : "2015-08-26T08:19:10.414",
      "generationTimeUTC" : "2015-08-26T08:18:53.410",
      "watchLow" : 10.0,
      "watchHigh" : 12.0,
      "warningLow" : 30.0,
      "warningHigh" : 32.0,
      "distressLow" : 40.0,
      "distressHigh" : 42.0,
      "criticalLow" : 60.0,
      "criticalHigh" : 62.0,
      "severeLow" : 80.0,
      "severeHigh" : 82.0,
      "expirationTime" : 1440577187914,
      "expirationTimeUTC" : "2015-08-26T08:19:11.914"
    },
    "violations" : 102
  } ]
}
{% endhighlight %}
