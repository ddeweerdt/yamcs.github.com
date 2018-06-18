---
layout: default
permalink: /docs/server/TM_DataLinks/
sidebar: yes
---

TM data links are components that collect data from external sources and inject them into a Yamcs stream. They are defined in the instance configuration file as part of the <tt>tmDataLinks</tt> list.

Each TM Provider is defined in terms of an identifying name, a class (the java class instantiated by Yamcs to load the provider), a specification (used as an argument when instantiating the class) and the name of the stream where the data will be injected. There is also a property <tt>enabledAtStartup</tt> which allows to enable (default) or disable the TM provider for connecting to the external data source at the server start-up.

An example configuration:
<pre>
<code class="config-file">
tmDataLinks:
    - class: org.yamcs.tctm.TcpTmDataLink
      name: tm_realtime
      args: local
      stream: tm_realtime
    - class: org.yamcs.tctm.TcpTmDataLink
      name: tm_dump
      args: localDump
      stream: tm_dump
</code>
</pre>

Yamcs provides by default the following TM Providers:

- org.yamcs.tctm.TcpTmDataLink
- org.yamcs.tctm.UdpTmDataLink
- org.yamcs.tctm.ArtemisTmDataLink
- org.yamcs.tctm.FilePollingTmDataLink

### org.yamcs.tctm.TcpTmDataLink
Provides packets received via plain TCP sockets. The packets in CCSDS format are expected one after the other without any delimiter or separator (the length is deduced from the CCSDS header).

The specification consists of a name which selects a configuration defined in the file [etc/tcp.yaml](/docs/server/tcp.yaml/).

In case the TCP connection with the telemetry server cannot be opened or is broken, it retries to connect each 10 seconds.


### org.yamcs.tctm.UdpTmDataLink
This class listens to a UDP port for datagrams containing CCSDS packets. It supports the following arguments:

<dl>
  <dt><tt>port</tt></dt>
  <dd>The UDP port to listen to.</dd>

  <dt><tt>maxLength</tt></dt>
  <dd>The maximum length of the packets received. If a larger datagram is received, the data will be truncated. Default: 1500 bytes</dd>
</dl>


Example usage:
<pre>
<code class="config-file">
tmDataLinks:
    - class: org.yamcs.tctm.UdpTmDataLink
      name: tm_realtime
      stream: tm_realtime
      args: 
          port: 5900
          maxLength: 2048
</code>
</pre>



### org.yamcs.tctm.FilePollingTmDataLink
This class reads data from files in a directory, importing it into the configured stream. The directory is polled regularely for new files and the files are imported one by one. After the import, the file is removed (if the option deleteAfterImport is not set to false, see below).

The following arguments are supported:

<dl>
  <dt><tt>incomingDir</tt></dt>
  <dd>The directory where the data will be read from. If not specified, the data will be read from <tt>&lt;yamcs-incoming-dir&gt;/&lt;instance&gt;/tm/</tt> where <tt>yamcs-incoming-dir</tt> is the value of the incomingDir property from <a href="/docs/server/yamcs.yaml">etc/yamcs.yaml</a>.</dd>

  <dt><tt>deleteAfterImport</tt></dt>
  <dd>Remove the file after importing all the data. By default set to true, can be set to false to import the same data again and again.</dd>

  <dt><tt>delayBetweenPackets</tt></dt>
  <dd>When importing a file, wait this many milliseconds after each packet. This option together with the previous one can be used to simulate incoming realtime data.</dd>
</dl>


### org.yamcs.tctm.ArtemisTmDataLink
This class reads data from an Artemis queue. Upon startup, the class will create the queue and bind it to the address which is specified in the spec parameter.

