---
layout: default
permalink: /docs/http/List_Events/
sidebar: yes
---

List the history of events:

    GET /api/archive/:instance/events/

### Parameters

<table class="inline">
    <tr>
        <th>Name</th>
        <th>Type</th>
        <th>Description</th>
    </tr>
    <tr>
        <td class="code">severity</td>
        <td class="code">string</td>
        <td>
            The minimum severity level of the events. One of <tt>info</tt>, <tt>watch</tt>, <tt>warning</tt>, <tt>distress</tt>, <tt>critical</tt> or <tt>severe</tt>. Default: <tt>info</tt>
        </td>
    </tr>
    <tr>
        <td class="code">q</td>
        <td class="code">string</td>
        <td>Text to search for in the message.</td>
    </tr>
    <tr>
        <td class="code">source</td>
        <td class="code">array of strings</td>
        <td>
            The source of the events. Both these notations are accepted:
            <ul>
                <li><tt>?source=DataHandler,CustomAlgorithm</tt></li>
                <li><tt>?source[]=DataHandler&source[]=CustomAlgorithm</tt></li>
            </ul>
            Names must match exactly.
        </td>
    </tr>
    <tr>
        <td class="code">start</td>
        <td class="code">string</td>
        <td>Filter the lower bound of the event's generation time. Specify a date string in ISO 8601 format. This bound is inclusive.</td>
    </tr>
    <tr>
        <td class="code">stop</td>
        <td class="code">string</td>
        <td>Filter the upper bound of the event's generation time. Specify a date string in ISO 8601 format. This bound is exclusive.</td>
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

The <tt>pos</tt> and <tt>limit</tt> allow for pagination. Keep in mind that in-between two requests extra data may have been recorded, causing a shift of the results. This stateless operation does not provide a reliable mechanism against that, so address it by overlapping your <tt>pos</tt> parameter with rows of the previous query. In this example we overlap by 4:

    ?pos=0&limit=50&order=desc
    ?pos=45&limit=50&order=desc
    
An alternative is to download the events instead.

### Response

<pre class="header">
Status: 200 OK
</pre>

```json
{
  "event" : [ {
    "source" : "AlarmChecker",
    "generationTime" : 1447425863786,
    "receptionTime" : 1447425863786,
    "seqNumber" : 15,
    "type" : "IN_LIMITS",
    "message" : "Parameter /YSS/SIMULATOR/BatteryVoltage2 has changed to value 222",
    "severity" : "INFO",
    "generationTimeUTC" : "2015-11-13T14:43:47.786Z",
    "receptionTimeUTC" : "2015-11-13T14:43:47.786Z"
  } ]
}
```

### Alternative Media Types

#### CSV

Use HTTP header:

    Accept: text/csv
    
Or, add this query parameter to the URI: `format=csv`.
    
Response:

<pre class="header">
Status: 200 OK
Content-Type: text/csv
</pre>

```
Source  Generation Time Reception Time  Event Type      Event Text
AlarmChecker    2015-11-13T14:46:36.029Z 2015-11-13T14:46:36.029Z IN_LIMITS       Parameter /YSS/SIMULATOR/BatteryVoltage2 has changed to value 195
AlarmChecker    2015-11-13T14:46:29.784Z 2015-11-13T14:46:29.784Z IN_LIMITS       Parameter /YSS/SIMULATOR/BatteryVoltage2 has changed to value 196
AlarmChecker    2015-11-13T14:46:23.571Z 2015-11-13T14:46:23.571Z IN_LIMITS       Parameter /YSS/SIMULATOR/BatteryVoltage2 has changed to value 197
```

#### Protobuf

Use HTTP header:

    Accept: application/protobuf

Responses are of type:

{% proto rest/rest.proto %}
message ListEventsResponse {
  repeated yamcs.Event event = 1;
}
{% endproto %}
