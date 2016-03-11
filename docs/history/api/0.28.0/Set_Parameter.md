---
layout: default
version: 0.28.0
permalink: /docs/api/0.28.0/Set_Parameter/
sidebar: yes
---

### HTTP Post

```
/{yamcsInstance}/api/parameter/_set
```

### Required Parameters

<table class="inline">
    <tr><th>Parameter</th><th>Description</th></tr>
     <tr><td>Body</td><td>Request body of type `Rest.ParameterData`</td></tr>
</table>


Protobuf definitions:

```proto
message ParameterData {
    repeated ParameterValue parameter=1;

    // the next three fields are used by the recorder as unique key to store parameters in "rows" 
    // and also by the components that provide parameters from external sources
    // the time should roughly correspond to the parameter time but can be rounded for better efficiency
    optional string group = 2;
    optional int64  generationTime = 3;
    optional int32 seqNum = 4;
}
```


```proto
message ParameterValue {
    optional yamcs.NamedObjectId id=1;
  	optional yamcs.Value rawValue=2;
	optional yamcs.Value engValue=3;
	optional int64 acquisitionTime=4;
	optional int64 generationTime=5;
	optional AcquisitionStatus acquisitionStatus=6;
	optional bool processingStatus=7;
	optional MonitoringResult monitoringResult=8;

    //to be used as alternative to the ones above for clients that do not understand internal yamcs time encoding
    optional string acquisitionTimeUTC = 11;
    optional string generationTimeUTC = 12;

    // Not transferring xtce.FloatRange to proto since we actually have some logic there
    optional double watchLow = 13;
    optional double watchHigh = 14;
    optional double warningLow = 15;
    optional double warningHigh = 16;
    optional double distressLow = 17;
    optional double distressHigh = 18;
    optional double criticalLow = 19;
    optional double criticalHigh = 20;
    optional double severeLow = 21;
    optional double severeHigh = 22;
    optional int64 expirationTime = 23;
    optional string expirationTimeUTC = 24;
}
```

```proto
message Value {
    enum Type {
        FLOAT = 0;
        DOUBLE = 1;
        UINT32 = 2;
        SINT32 = 3;
        BINARY = 4;
        STRING = 5;
        TIMESTAMP = 6;
        UINT64 = 7;
        SINT64 = 8;
        BOOLEAN = 9;
    };
    required Type type=1;
    optional float         floatValue=2;
    optional double        doubleValue=3;
    optional sint32        sint32Value=4;
    optional uint32        uint32Value=5;
    optional bytes         binaryValue=6;
    optional string        stringValue=7;
    optional int64         timestampValue=8;
    optional uint64        uint64Value=9;
    optional sint64        sint64Value=10;
    optional bool          booleanValue=11;
}
```

```proto
enum AcquisitionStatus {
      ACQUIRED=0; //OK!
      NOT_RECEIVED=1; //no value received so far
      INVALID=2; //some value has been received but is invalid
      EXPIRED=3; //the parameter is coming from a packet which has not since updated although it should have been
};
```


```proto
enum MonitoringResult {
      DISABLED=0;
      IN_LIMITS=1;
      // NOMINAL_LIMIT_VIOLATION=2;
      // NOMINAL_LOW_LIMIT_VIOLATION=3;
      // NOMINAL_HIGH_LIMIT_VIOLATION=4;
      // DANGER_LOW_LIMIT_VIOLATION=5;
      // DANGER_HIGH_LIMIT_VIOLATION=6;
      WATCH=7;
      WATCH_LOW=8;
      WATCH_HIGH=9;
      WARNING=10;
      WARNING_LOW=11;
      WARNING_HIGH=12;
      DISTRESS=13;
      DISTRESS_LOW=14;
      DISTRESS_HIGH=15;
      CRITICAL=16;
      CRITICAL_LOW=17;
      CRITICAL_HIGH=18;
      SEVERE=19;
      SEVERE_LOW=20;
      SEVERE_HIGH=21;
}
```


### Optional Parameters

### Response

Empty response.

### Example


