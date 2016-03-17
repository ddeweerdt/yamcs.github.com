---
layout: default
permalink: /docs/server/PP_DataLinks/
sidebar: yes
---

PP Data Links are components that collect processed parameters (PP) from external sources and inject them into a Yamcs stream. They are defined in the instance configuration file as part of the <tt>ppDataLinks</tt> list.

Each PP data link is defined in terms of an identifying name, a class (the java class instantiated by Yamcs to load the provider), a specification (used as an argument when instantiating the class) and the name of the stream where the data will be injected. There is also a property <tt>enabledAtStartup</tt> which allows to enable (default) or disable the PP provider for connecting to the external data source at the server start-up.



### MulticastPpProvider
Implements processed parameters received via multicast from the TMR

At start-up the MulticastPpProvider loads configuration properties defined in the configuration file [etc/multicast.yaml](/docs/server/multicast.yaml). It builds the list of processed parameters which have to be considered from the MDB taking all the UMI tables found in the configured CCU.

The processed parameters are sent by TMR packetized in packets of variable size. Each packet is received in a UDP datagram.

The MulticastPpProvider uses some classes from the DaSS API to decode these packets which are then made available to the clients using the same mechanism and the same DaSS to CIS mapping like the DassPpProvider. The parameters which are not defined in the UMI maps loaded from the MDB are discarded.

Using [Yamcs Studio](/docs/studio/) or [Yamcs Monitor](/docs/tools/Yamcs_Monitor/) the processing of packets can be enabled/disabled. In addition the MulticastPpProvider collects simple statistics with the number of UDP datagrams received and the number of processed parameters in the last datagram. These statistics can also be seen using the Yamcs Monitor.

### SimulationPpProvider
Some tests request data to be simulated. This can be achieved by using the SimulationPpProvider. The SimulationPpProvider takes as input scenarios that are defined in XML files.

The XML scenario file allows to describe the parameters sent, their generation time, acquisition time, engineering value and monitoring value. Parameters are organized in a sequence that can be repeated to allow more complex scenarios. The speed of the simulation can be defined, by setting the duration of a simulation step.

