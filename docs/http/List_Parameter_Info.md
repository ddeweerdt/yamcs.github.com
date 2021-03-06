---
layout: default
permalink: /docs/http/List_Parameter_Info/
sidebar: yes
---

List all parameters defined in the Mission Database for the given Yamcs instance:

    GET /api/mdb/:instance/parameters

### Parameters

<table class="inline">
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td class="code">namespace</td>
    <td class="code">string</td>
    <td>Include parameters under the specified namespace only</td>
  </tr>
  <tr>
    <td class="code">recurse</td>
    <td class="code">bool</td>
    <td>If a <tt>namespace</tt> is given, specifies whether to list parameters of any nested sub systems. Default <tt>no</tt>.</td>
  </tr>
  <tr>
    <td class="code">type</td>
    <td class="code">array of strings</td>
    <td>
        The parameter types to be included in the result. Valid types are <tt>boolean</tt>, <tt>binary</tt>, <tt>enumeration</tt>, <tt>float</tt>, <tt>integer</tt> or <tt>string</tt>. Both these notations are accepted:
        <ul>
            <li><tt>?type=float,integer</tt></li>
            <li><tt>?type[]=float&type[]=integer</tt></li>
        </ul>
        If unspecified, parameters of all types will be included.
    </td>
  </tr>
  <tr>
    <td class="code">q</td>
    <td class="code">string</td>
    <td>The search keywords.</td>
  </tr>
  <tr>
    <td class="code">pos</td>
    <td class="code">integer</td>
    <td>The zero-based row number at which to start outputting results. Default: <tt>0</tt></td>
  </tr>
  <tr>
    <td class="code">limit</td>
    <td class="code">integer</td>
    <td>The maximum number of returned parameters per page. Choose this value too high and you risk hitting the maximum response size limit enforced by the server. Default: <tt>100</tt></td>
  </tr>
</table>

The `q` parameter supports searching on namespace or name. For example:

    /api/mdb/simulator/parameters?q=ccsds+yss


### Response

<pre class="header">Status: 200 OK</pre>
```json
{
  "parameter" : [ {
    "name": "ccsds-apid",
    "qualifiedName" : "/YSS/ccsds-apid",
    "alias" : [ {
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
  } ]
}
```


### Alternative Media Types

#### Protobuf

Use HTTP header:

    Accept: application/protobuf
    
Response is of type:

{% proto rest/rest.proto %}
message ListParameterInfoResponse {
  repeated mdb.ParameterInfo parameter = 1;
}
{% endproto %}
