---
layout: default
permalink: /docs/server/TM_Providers/
sidebar: yes
---

TM Providers are components that collect data from external sources and inject them into a Yamcs stream. They are defined in the instance configuration file as part of the `tmProviders` list.

Each TM Provider is defined in terms of a name (which allows identifying it in the Yamcs Monitor), a class (the java class instantiated by Yamcs to load the provider), a specification (used as an argument when instantiating the class) and the name of the stream where the data will be injected. There is also a property `enabledAtStartup` which allows to enable (default) or disable the TM provider for connecting to the external data source at the server startup.

### DassPacketProvider
Receives telemetry packets (PathTM) from DaSS. 

At startup the DassPacketProvider loads configuration properties defined in the configuration file `dass.yaml`. It builds the list of packet specifications which it should subscribe to DaSS. A specification is an object (vehicle id, packet type, apid, private header source). The list is built as follows:

* If the property `tmSubscriptionList` is defined, then it considers only the specifications matching this property.
* If the property `tmSubscriptionList` is not defined, then all the APIDs defined in the MDB are considered as part of the subscription list with the vehicle id set to 2 (=Columbus), the packet type set to 1 (=payload) and the private header source set to -1 (=all). Please note that this kind of subscription only works when connected to the DaSS kernel not when connected to the USOC router (the USOC router does not support the wildcard subscriptions).

Once the subscription list is built, the DassPacketProvider regularly tries to subscribe all the unsubscribed specifications from the list. At any time the Yamcs Monitor can be used to inspect the status of the subscription list. The Yamcs Monitor can also be used to close/re-open the connection to DaSS.

#### Secure Connections and Certificates
If the property `certificate` is specified, it has to point to a certificate file which will be then used by the DassPacketProvider (also the DassPpProvider and the DassTcUplinker) to connect to DaSS (or to the USOC router) in an encrypted way. Unlike the TMR in CD-MCS, the DassPacketProvider will try to verify the certificate of the server (using java built-in mechanism). Normally the Yamcs Server is started (by the script `yamcs-server.sh`) with the additional flag:

    -Djavax.net.ssl.trustStore=yamcs_root_directory/etc/trustStore
    
 This option configures java to trust the certificates signed with the certificates stored in the trustStore file.

For the secure connection to work, the file `etc/trustStore` has to be populated with the key which has signed the DaSS server key. This can be easily done using the command *keytool* delivered as part of the Java distribution:

    keystore -import -alias esa_root -keystore etc/trustStore -file esa_root.crt

This command will import the file `esa_root.crt` into the java key store.

### TcpTmProvider
Provides packets received via plain TCP sockets. The packets in CCSDS format are expected one after the other without any delimiter or separator (the length is deduced from the CCSDS header).

The specification consists of a name which selects a configuration defined in the file `tcp.yaml`.

In case the tcp connection with the telemetry server cannot be opened or is broken, it retries to connect each 10 seconds.

### TmapTmProvider
This provider is very similar with the TcpTmProvider above except that it expects packets having an extra 32 bytes PaCTS header followed by the CCSDS header. The PaCTS header is discarded.


### MulticastTmProvider
This provider listens to a multicast (or UDP) port for datagrams containing CCSDS packets.

The specification consists of a name which selects a configuration defined in the file `multicast.yaml`
