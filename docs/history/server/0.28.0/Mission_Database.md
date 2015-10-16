---
layout: default
sidebar: yes
chapter: yes
version: 0.28.0
permalink: /docs/server/0.28.0/Mission_Database/
---

The Yamcs Mission Database is composed of the following parts, contained in an XTCE hierarchical structure:

* Telemetry
* Telecommands
* Processed Parameters
* Algorithms

For faster access, the database is cached serialized on disk in the cache directory. The cached mission database is composed of two files, one storing the data itself and the other one storing the time when the cache file has been created. These files should be considered Yamcs internal and are subject to change.
 
Different loaders are possible for each database source type.
