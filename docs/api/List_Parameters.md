---
layout: default
permalink: /docs/api/List_Parameters/
sidebar: yes
---

List all parameters defined in the Mission Database for the given Yamcs instance:

    GET /api/:instance/parameters


List all parameters defined under the given namespace:

    GET /api/:instance/parameters/:namespace
    
In case of fully qualified XTCE names, the `:namespace` segment must be repeated for every nested space system.

For example these URIs are all valid:

    /api/simulator/parameters/MDB%3AOPS+Name
    /api/simulator/parameters/YSS/SIMULATOR
    
Notice the use of `%3A` and `+` to URL-encode `MDB:OPS Name` to the ASCII character set. The server supports UTF-8 but your client may not.


### Parameters

<table class="inline">
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td class="code">q</td>
    <td class="code">string</td>
    <td>The search keywords.</td>
  </tr>
  <tr>
    <td class="code">pretty</td>
    <td class="code">bool</td>
    <td>Format the JSON result in a human readable manner.</td>
  </tr>
</table>

The `q` parameter supports searching on namespace or name. For example:

    /api/simulator/parameters?q=ccsds+yss&pretty 


### Response

{% highlight json %}
{
  "parameter" : [ {
    "description" : {
      "qualifiedName" : "/YSS/ccsds-apid",
      "aliases" : [ {
        "name" : "YSS_ccsds-apid",
        "namespace" : "MDB:OPS Name"
      }, {
        "name" : "ccsds-apid",
        "namespace" : "/YSS"
      } ]
    },
    "type" : {
      "engType" : "integer",
      "dataEncoding" : "IntegerDataEncoding(sizeInBits:11, encoding:unsigned, defaultCalibrator:null byteOrder:BIG_ENDIAN)"
    },
    "dataSource" : "TELEMETERED",
    "url" : "http://localhost:8090/api/simulator/parameters/YSS/ccsds-apid"
  } ]
}
{% endhighlight %}


### Protobuf

Response body is of type `Parameters.ListParametersResponse`

{% highlight nginx %}
message ListParametersResponse {
  repeated ParameterInfo parameter = 1;
}
{% endhighlight %}

Supporting definitions:

{% highlight nginx %}
message ParameterInfo {
  optional NameDescriptionInfo description = 2;
  optional ParameterTypeInfo type = 3;
  optional DataSourceType dataSource = 4;
  optional string url = 5;
}
{% endhighlight %}

{% highlight nginx %}
message NameDescriptionType {
  optional string qualifiedName = 1;
  optional string shortDescription = 2;
  optional string longDescription = 3;
  repeated yamcs.NamedObjectId aliases = 4;
}
{% endhighlight %}

{% highlight nginx %}
message ParameterTypeInfo {
  optional string engType = 1;
  optional string dataEncoding = 2;
  repeated UnitInfo unitSet = 3; 
  optional AlarmInfo defaultAlarm = 4;
}
{% endhighlight %}

{% highlight nginx %}
message UnitInfo {
  optional string unit = 1;
}
{% endhighlight %}

{% highlight nginx %}
message AlarmInfo {
  optional int32 minViolations = 1;
  repeated AlarmRange staticAlarmRanges = 2;
}
{% endhighlight %}

{% highlight nginx %}
message AlarmRange {
  optional AlarmLevel level = 1; 
  optional double minInclusive = 2;
  optional double maxInclusive = 3; 
  optional string enumerationValue = 4;
}
{% endhighlight %}

{% highlight nginx %}
enum AlarmLevel {
  NORMAL = 0;
  WATCH = 1;
  WARNING =  2;
  DISTRESS = 3;
  CRITICAL = 4;
  SEVERE = 5;
}
{% endhighlight %}

{% highlight nginx %}
enum DataSourceType {
  TELEMETERED = 0;
  DERIVED = 1;
  CONSTANT = 2;
  LOCAL = 3;
  SYSTEM = 4;
  COMMAND = 5;
  COMMAND_HISTORY = 6;
}
{% endhighlight %}
