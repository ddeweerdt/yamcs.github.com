---
layout: default
permalink: /docs/server/Commanding/
sidebar: yes
---

Yamcs contains an HLCL parser capable to parse the telecommanding requests coming from the MCS Tools. 

XTCE structures are not supported for commanding, and neither are command preconditions or postconditions (i.e. checking that telemetry parameters have certain values before or after sending the command).


#### Command Queues
In Yamcs when a command is sent by the CIS client it doesn't go directly to the TcUplinker but instead it goes into a queue. Privileges are checked before the command is put into the queue, so if the user doesn't have the privilege for the given telecommand, the command will be rejected and not appear at all in the queue. In fact, the command is already rejected when the prepareCommand CORBA call is made. This means that a user will not be able to open using the MCS Tools a stack containing a command for which he does not have authorization.

The available queues are defined in the file `etc/commandqueue.yaml` (see <xref linkend="command-queue.yaml"/>).

Each queue has a name, a default state and a list of roles. The commands of a user logging in with a given role will be put in the first queue for which the role is specified. A queue can be in three different states:

<table class="inline">
    <tr>
        <th>Enabled</th>
        <td>means the commands are sent immediately</td>
    </tr>
    <tr>
        <th>Blocked</th>
        <td>means the commands are accepted into the queue but need to be manually sent</td>
    </tr>
    <tr>
        <th>Disabled</th>
        <td>means the commands are rejected</td>
    </tr>
</table>

There is always a command-queue called 'default' whose state is enabled. If a command comes from a user whose role is not defined by any other queue (not recommended), the command will be put in the default queue. The default queue can be redefined in the `command-queue.yaml` in order to have a different state.

The content of the command queue can be inspected using the Yamcs Monitor as explained <xref linkend="command-queue-control"/>. To be able to control the Command Queues, the user needs the MayControlCommandQueue privilege.
