---
layout: default
sidebar: yes
version: 0.28.0
permalink: /docs/server/0.28.0/privileges.yaml/
---

<pre>
<code class="config-file">
#configuration of the privileges
# if privileges.enabled is set to false, the connection to realm is not even
# attempted and hasPrivilege method always returns true
#
# if privileges.enables is set to true, you need to enable security of hornetQ and ensure
# the hornetQ roles are assigned to user in the chosen realm.
enabled: false

#one of: LdapRealm, YamlRealm
realm: org.yamcs.security.YamlRealm

#maximum number of CIS sessions clients are allowed
maxNoSessions: 10

ldaphost:        host
userPath:        "ou=People,o=usoc"
rolePath:        "ou=Roles, ou=Operation, ou=Columbus,ou=Projects,o=usoc"
systemPath:      "ou=System, ou=yamcs, ou=Applications, ou=Operation, ou=Columbus,ou=Projects,o=usoc"
tmParameterPath: "ou=TM_PARAMETER, ou=yamcs, ou=Applications, ou=Operation, ou=Columbus,ou=Projects,o=usoc"
tmPacketPath:    "ou=TM_PACKET, ou=yamcs, ou=Applications, ou=Operation, ou=Columbus,ou=Projects,o=usoc"
tcPath:          "ou=TC, ou=yamcs, ou=Applications, ou=Operation, ou=Columbus,ou=Projects,o=usoc"

# yaml file, if using YamlRealm
yamlRealmFilename:  credentials.yaml
</code>
</pre>
