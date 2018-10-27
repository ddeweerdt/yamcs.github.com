---
layout: default
permalink: /docs/http/Get_Command_Info/
sidebar: yes
---

Return the data for the given command:

    GET /api/mdb/:instance/commands/:namespace/:name


### Response

<pre class="header">Status: 200 OK</pre>
```json
{
  "name": "SWITCH_VOLTAGE_ON",
  "qualifiedName" : "/YSS/SIMULATOR/SWITCH_VOLTAGE_ON",
  "alias" : [ {
    "name" : "SIMULATOR_SWITCH_VOLTAGE_ON",
    "namespace" : "MDB:OPS Name"
  }, {
    "name" : "SWITCH_VOLTAGE_ON",
    "namespace" : "/YSS/SIMULATOR"
  } ],
  "baseCommand" : {
    "name": "SIM_TC",
    "qualifiedName" : "/YSS/SIMULATOR/SIM_TC",
    "alias" : [ {
      "name" : "SIMULATOR_SIM_TC",
      "namespace" : "MDB:OPS Name"
    }, {
      "name" : "SIM_TC",
      "namespace" : "/YSS/SIMULATOR"
    } ],
    "baseCommand" : {
      "name": "ccsds-tc",
      "qualifiedName" : "/YSS/ccsds-tc",
      "alias" : [ {
        "name" : "YSS_ccsds-tc",
        "namespace" : "MDB:OPS Name"
      }, {
        "name" : "ccsds-tc",
        "namespace" : "/YSS"
      } ],
      "abstract" : true,
      "argument" : [ {
        "name" : "ccsds-apid",
        "type" : "integer"
      }, {
        "name" : "timeId",
        "type" : "integer"
      }, {
        "name" : "checksumIndicator",
        "type" : "integer",
        "initialValue" : "1"
      }, {
        "name" : "packet-type",
        "type" : "integer"
      }, {
        "name" : "packet-id",
        "type" : "integer"
      } ]
    },
    "abstract" : true,
    "argumentAssignment" : [ {
      "name" : "ccsds-apid",
      "value" : "100"
    }, {
      "name" : "timeId",
      "value" : "1"
    }, {
      "name" : "packet-type",
      "value" : "10"
    } ]
  },
  "abstract" : false,
  "argument" : [ {
    "name" : "voltage_num",
    "description" : "voltage number to switch on",
    "type" : "integer",
    "unitSet" : [ {
      "unit" : "V"
    } ]
  } ],
  "argumentAssignment" : [ {
    "name" : "packet-id",
    "value" : "1"
  } ]
}
```

### Alternative Media Types

#### Protobuf

Use HTTP header:

    Accept: application/protobuf

Response is of type:

<pre class="r header"><a href="{{ site.proto }}/mdb/mdb.proto">mdb.proto</a></pre>
```proto
message CommandInfo {
  optional string name = 1;
  optional string qualifiedName = 2;
  optional string shortDescription = 3;
  optional string longDescription = 4;
  repeated yamcs.NamedObjectId alias = 5;
  optional CommandInfo baseCommand = 6;
  optional bool abstract = 7;
  repeated ArgumentInfo argument = 8;
  repeated ArgumentAssignmentInfo argumentAssignment = 9;
  optional SignificanceInfo significance = 10;
  repeated TransmissionConstraintInfo constraint = 11;
}
```
