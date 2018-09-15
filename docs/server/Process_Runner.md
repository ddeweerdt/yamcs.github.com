---
layout: default
permalink: /docs/server/Process_Runner/
sidebar: yes
---

Runs an external process. If this process goes down, a new process instance is started.

### Class Name
[<tt>org.yamcs.server.ProcessRunner</tt>](https://javadoc.io/page/org.yamcs/yamcs-server/latest/org/yamcs/server/ProcessRunner.html)

### Configuration

This is a global service defined in <tt>etc/yamcs.yaml</tt>. Example from a typical deployment:

<pre class="r header">yamcs.yaml</pre>
```yaml
services:
  - class: org.yamcs.server.ProcessRunner
    args:
      command: "bin/simulator.sh"
```

### Configuration Options

<table class="inline">
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td class="code">command</td>
    <td class="code">string</td>
    <td><strong>Required. </strong> Command to run.</td>
  </tr>
  <tr>
    <td class="code">directory</td>
    <td class="code">string</td>
    <td>Directory where to run the command from. If unspecified, this defaults to the cwd of Yamcs.</td>
  </tr>
  <tr>
    <td class="code">logLevel</td>
    <td class="code">string</td>
    <td>Level at which to log stdout/stderr output. One of <tt>INFO</tt>, <tt>DEBUG</tt>, <tt>TRACE</tt>, <tt>WARN</tt>, <tt>ERROR</tt>. Default: <tt>INFO</tt></td>
  </tr>
  <tr>
    <td class="code">logPrefix</td>
    <td class="code">string</td>
    <td>Prefix to prepend to all logged process output. If unspecified this defaults to '<tt>[COMMAND] </tt>'.</td>
  </tr>
</table>
