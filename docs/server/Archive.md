---
layout: default
sidebar: yes
chapter: yes
permalink: /docs/server/Archive/
---
The Yamcs archive is divided in two parts:

* <b>Stream Archive</b> stores time ordered tuples (t, v<sub>1</sub>, v<sub>2</sub>...v<sub>n</sub>) where t is the time and v<sub>1</sub>, v<sub>2</sub>, v<sub>n</sub> are values of various types. This is used for storing raw telemetry packets, commands, events, alarms and processed parameters. The stream archive can be seen as a row-oriented archive and is optimized for accessing entire records (e.g. a packet or a group of processed parameters).

* <b>Parameter Archive</b> stores time ordered parameter values. The parameter archive is column oriented archive and it is optimized for accessing a (relatively small) number of parameters over longer periods of time.

Data is stored in the Stream Archive as soon as it is being received, whereas the Parmeter Archive involves some data transformation and it is filled in batches. However, for an external user, Yamcs should make the filling process invisible so data from both archives can be retrieved (almost) as soon as it been received by Yamcs.
