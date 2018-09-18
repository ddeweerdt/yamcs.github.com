---
layout: default
permalink: /docs/server/Artemis_Parameter_Data_Link/
sidebar: yes
---

Reads <tt>param</tt> data from an Artemis queue and publishes it to the configured stream.

### Class Name
[<tt>org.yamcs.tctm.ArtemisParameterDataLink</tt>](https://javadoc.io/page/org.yamcs/yamcs-core/latest/org/yamcs/tctm/ArtemisParameterDataLink.html)

### Configuration Options

<table class="inline">
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td class="code">stream</td>
    <td class="code">string</td>
    <td><b>Required.</b> The stream where data is emitted</td>
  </tr>
  <tr>
    <td class="code">address</td>
    <td class="code">string</td>
    <td>
      Artemis address to bind to.
    </td>
  </tr>
</table>
