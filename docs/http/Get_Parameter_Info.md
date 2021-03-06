---
layout: default
permalink: /docs/http/Get_Parameter_Info/
sidebar: yes
---

Return the data for the given parameter:

    GET /api/mdb/:instance/parameters/:namespace/:name


### Response

<pre class="header">Status: 200 OK</pre>
```json
{
  "name": "BatteryVoltage2",
  "qualifiedName" : "/YSS/SIMULATOR/BatteryVoltage2",
  "alias" : [ {
    "name" : "SIMULATOR_BatteryVoltage2",
    "namespace" : "MDB:OPS Name"
  }, {
    "name" : "BatteryVoltage2",
    "namespace" : "/YSS/SIMULATOR"
  } ],
  "type" : {
    "engType" : "integer",
    "dataEncoding" : "IntegerDataEncoding(sizeInBits:8, encoding:unsigned, defaultCalibrator:null byteOrder:BIG_ENDIAN)"
  },
  "dataSource" : "TELEMETERED"
}
```


### Bulk

Combine multiple parameter queries in one and the same request using this address:

    GET /api/mdb/:instance/parameters/bulk
    
Specify the parameter IDs in the request body:

```json
{
  "id" : [ {
    "name": "YSS_ccsds-apid",
    "namespace": "MDB:OPS Name"
  }, {
    "name": "YSS_packet-type",
    "namespace": "MDB:OPS Name"
  } ]
}
```

POST requests are also allowed, because some HTTP clients do not support GET with a request body.

In the response the requested parameter ID is returned for every match. Example:

```json
{
  "response" : [ {
    "id" : {
      "name" : "YSS_ccsds-apid",
      "namespace" : "MDB:OPS Name"
    },
    "parameter" : {
      "name": "ccsds-apid",
      "qualifiedName" : "/YSS/ccsds-apid",
      "aliases" : [ {
        "name" : "YSS_ccsds-apid",
        "namespace" : "MDB:OPS Name"
      }, {
        "name" : "ccsds-apid",
        "namespace" : "/YSS"
      } ],
      "type" : {
        "engType" : "integer",
        "dataEncoding" : "IntegerDataEncoding(sizeInBits:11, encoding:unsigned, defaultCalibrator:null byteOrder:BIG_ENDIAN)"
      },
      "dataSource" : "TELEMETERED"
    }
  } ]
}
``` 


### Alternative Media Types

#### Protobuf

Use these HTTP headers:

    Content-Type: application/protobuf
    Accept: application/protobuf
    
Response is of type:

{% proto mdb/mdb.proto %}
message ParameterInfo {
  optional string name = 1;
  optional string qualifiedName = 2;
  optional string shortDescription = 3;
  optional string longDescription = 4;
  repeated yamcs.NamedObjectId alias = 5;
  optional ParameterTypeInfo type = 6;
  optional DataSourceType dataSource = 7;
}
{% endproto %}

Bulk request is of type:

{% proto rest/rest.proto %}
message BulkGetParameterRequest {
  repeated yamcs.NamedObjectId id = 1;
}
{% endproto %}

Bulk response is of type:

{% proto rest/rest.proto %}
message BulkGetParameterResponse {
  message GetParameterResponse {
    optional yamcs.NamedObjectId id = 1;
    optional mdb.ParameterInfo parameter = 2;
  }

  repeated GetParameterResponse response = 1;
}
{% endproto %}
