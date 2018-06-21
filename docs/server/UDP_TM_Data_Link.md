---
layout: default
permalink: /docs/server/UDP_TM_Data_Link/
sidebar: yes
---

Listens on a UDP port for datagrams containing CCSDS packets. One datagram is equivalent to one packet.

### Class Name
[<tt>org.yamcs.tctm.UdpTmDataLink</tt>](https://javadoc.io/page/org.yamcs/yamcs-core/latest/org/yamcs/tctm/UdpTmDataLink.html)

### Configuration Options

<dl>
  <dt>port</dt>
  <dd><b>Required.</b> The UDP port to listen on</dd>

  <dt>maxLength</dt>
  <dd>The maximum length of the packets received. If a larger datagram is received, the data will be truncated. Default: 1500 bytes</dd>

  <dt>packetPreprocessorClassName</dt>
  <dd>
    Class name of a <a href="https://javadoc.io/page/org.yamcs/yamcs-core/latest/org/yamcs/tctm/PacketPreprocessor.html">PacketPreprocessor</a> implementation. Default is <a href="https://javadoc.io/page/org.yamcs/yamcs-core/latest/org/yamcs/tctm/IssPacketPreprocessor.html"><tt>org.yamcs.tctm.IssPacketPreprocessor</tt></a> which applies ISS conventions.
  </dd>

  <dt>packetPreprocessorArgs</dt>
  <dd>
    Optional args of arbitrary complexity to pass to the PacketPreprocessor. Each PacketPreprocessor may support different options.
  </dd>
</dl>
