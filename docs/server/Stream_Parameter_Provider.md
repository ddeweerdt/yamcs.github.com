---
layout: default
permalink: /docs/server/Stream_Parameter_Provider/
sidebar: yes
---

Provides parameters received from the configured <tt>param</tt> stream.

### Class Name
[<tt>org.yamcs.tctm.StreamParameterProvider</tt>](https://javadoc.io/page/org.yamcs/yamcs-core/latest/org/yamcs/tctm/StreamParameterProvider.html)

### Configuration

This service is defined in <tt>etc/processor.yaml</tt>. Example:

<pre class="r header">processor.yaml</pre>
```yaml
realtime:
  services:
    - class: org.yamcs.tctm.StreamParameterProvider
      args:
        stream: "pp_realtime"
```

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
    <td><strong>Required.</strong> The stream to read.</td>
  </tr>
</table>
