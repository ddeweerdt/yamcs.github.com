---
layout: default
permalink: /docs/server/Simulated_Parameter_Data_Link/
sidebar: yes
---

Some tests require parameter data to be simulated without using a packet source. This can be achieved by using the SimulationPpProvider. The SimulationPpProvider takes as input scenarios that are defined in XML files.

The XML scenario file allows to describe the parameters sent, their generation time, reception time, engineering value and monitoring value. Parameters are organized in a sequence that can be repeated to allow more complex scenarios. The speed of the simulation can be defined by setting the duration of a simulation step.

### Class Name
[<tt>org.yamcs.simulation.SimulationPpProvider</tt>](https://www.yamcs.org/yamcs/javadoc/index.html?org/yamcs/simulation/SimulationPpProvider.html)

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
    <td class="code">simulationDataPath</td>
    <td class="code">string</td>
    <td><b>Required.</b> Path to the XML file containing further configuration</td>
  </tr>
</table>
