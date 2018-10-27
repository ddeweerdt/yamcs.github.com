---
layout: default
permalink: /docs/server/Local_Parameter_Manager/
sidebar: yes
---

Manages and provides local parameters.

### Class Name
{% javadoc 'org/yamcs/parameter/LocalParameterManager' %}

### Configuration

This service is defined in <tt>etc/processor.yaml</tt>. Example:

<pre class="r header">processor.yaml</pre>
```yaml
realtime:
  services:
    - class: org.yamcs.parameter.LocalParameterManager
```
