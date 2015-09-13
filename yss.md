---
layout: default
title: Up & Running
permalink: /running/
weight: 20
top: yes
---

Yamcs deployment details can vary greatly from mission to mission. To present an overall feel of the core system, we have created a sample configuration, which we call the **Yamcs Simulation System (YSS)**.

# Yamcs Simulation System (YSS)

The YSS configuration is very simplistic by design, showcasing only core functionality. In the backend, it includes just two servers: **Yamcs** and a basic **Simulator**. These servers are set-up to exchange TM and TC. In the frontend, we connect sample operator displays that were authored in **Yamcs Studio**, as well as a selection of built-in displays (Archive, Command Stack, etc.). From Yamcs Studio we can send commands to Yamcs, which in turn will verify and issue them to the Simulator.

Running YSS is easy and straight-forward, but there are a few requirements you'll need to make sure your system has before you start. In particular this showcase uses `docker` and `docker-compose` to run container images that are prebuilt by the core Yamcs development team, and updated together with every Yamcs release.

## Install Docker

Detailed installation instructions can be found at [https://docs.docker.com/installation/](https://docs.docker.com/installation/). For example, on Ubuntu 14.04 LTS the simplest install would be something like:

    $ curl -sSL https://get.docker.com/ | sh
    
Docker's official documentation also explains how to set up `docker` so that you don't need to prepend every command with `sudo`, which we definitely recommend. Further instructions presume that `docker` was configured as such, and will no longer mention the use of `sudo`.

Verify correct installation by running `docker -v`. 

## Install Docker Compose

Detailed installation instructions can be found at [https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/). It boils down to this:

1. Get the `docker-compose` binary.

        $ sudo wget https://github.com/docker/compose/releases/download/1.4.0/docker-compose-`uname  -s`-`uname -m` -O /usr/local/bin/docker-compose

    This command installs the binary in the `/usr/local/bin` directory. 
	
2. Add executable permissions to the binary.

        $ sudo chmod +x /usr/local/bin/docker-compose
        
Verify correct installation by running `docker-compose -v`. Any problems related to this latest command usually have to do with either not having started the docker daemon (for some platforms this is automatically configured, for others not), or by not having added your user to the `docker` group. Please ask a yamcs developer for further assistance specific to your platform if you get stuck on this.
		
## Run the Yamcs Simulation System (YSS)

With all the preparations done, we now get to the real meat of running a Yamcs instance in a box (well, container).

1. Get the YSS configuration.

        $ curl -sSL http://www.yamcs.org/yss.sh | sh

    This will create a directory `yss` under your current working directory with some configuration files
    needed to link the Yamcs container with the Simulator container.

2. Start your YSS deployment with compose.

        $ cd yss
        $ docker-compose up
    
    This will launch both Yamcs and the Simulator in the foreground. You should see some log messages and the phrase  *yamcsstartup success* near the bottom.
    
     When you're done with testing and want to shutdown both servers, just `CTRL-c` this process. Later on, whenever you want the servers back up again, run `docker-compose up` -- you no longer need any of the other commands.

## Explore a bit

We now have a working yamcs server receiving and recording telemetry from a simulator. To get a better peek at what's happening we will now install Yamcs Studio -- a rich desktop client for Yamcs.
