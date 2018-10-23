---
layout: default
permalink: /downloads/
sidebar: no
title: Downloads
---

<!--
Yamcs open-source software is available via different package formats. Visit the appropriate product pages for installation instructions:

* [Yamcs Server](/docs/server/)
* [Yamcs Studio](/docs/studio/)
-->

{% assign latest = site.data.releases.yamcs.master[0] %}
### Yamcs Server {{ latest.tag_name | replace: 'yamcs-','v' }}

<table style="width: 100%;">
    <tr>
        <td style="width: 33.33%; text-align: center">
            <img src="/assets/tux.png" style="width: 70px; height: 70px; padding: 20px">
        </td>
        <td style="width: 33.33%"></td>
        <td style="width: 33.33%"></td>
    </tr>
    <tr>
        <td style="width: 33.33%; text-align: center">Linux x64</td>
        <td style="width: 33.33%"></td>
        <td style="width: 33.33%"></td>
    </tr>
    <tr>
        <td style="text-align: center">
            <a href="{{ latest.rpm.url }}">.rpm</a>&nbsp;&nbsp;
            <a href="{{ latest.tgz.url }}">.tar.gz</a>
        </td>
        <td></td>
        <td></td>
    </tr>
</table>

<p>&nbsp;</p>

{% assign latest = site.data.releases['yamcs-studio'].master[0] %}
### Yamcs Studio {{ latest.name }}

<table style="width: 100%;">
    <tr>
        <td style="text-align: center">
            <img src="/assets/windows.png" style="width: 70px; height: 70px; padding: 20px">
        </td>
        <td style="text-align: center">
            <img src="/assets/tux.png" style="width: 70px; height: 70px; padding: 20px">
        </td>
        <td style="text-align: center">
            <img src="/assets/apple.png" style="width: 70px; height: 70px; padding: 20px">
        </td>
    </tr>
    <tr>
        <td style="text-align: center"><a href="{{ latest.windows.url }}">Windows x64</a></td>
        <td style="text-align: center">Linux x64</td>
        <td style="text-align: center"><a href="{{ latest.macos.url }}">macOS</a></td>
    </tr>
    <tr>
        <td></td>
        <td style="text-align: center">
            <a href="https://nexus.spaceapplications.com/repository/yamcs/rpm/stable/x86_64/yamcs-studio-1.2.0-1.x86_64.rpm">.rpm</a>&nbsp;&nbsp;
            <a href="{{ latest.linux.url }}">.tar.gz</a>
        </td>
        <td></td>
    </tr>
</table>

<p>&nbsp;</p>

### Linux Signing Key

Yamcs RPM and Debian packages are signed with GNU Privacy Guard (GPG).

* Download: [https://nexus.spaceapplications.com/repository/yamcs/keys/yamcs.asc](https://nexus.spaceapplications.com/repository/yamcs/keys/yamcs.asc)
* Name: Yamcs Team
* Fingerprint: <tt>E74F A2E7 41D3 018E 5700  C729 16BF 99E3 A3B5 D542</tt>

<p>&nbsp;</p>

### Yum Repository

#### RPM (RHEL, Fedora, CentOS)

Packages suitable for x86_64 are available via a yum repository. The repository and key can be installed with the following script:

```shell
sudo rpm --import https://nexus.spaceapplications.com/repository/yamcs/keys/yamcs.asc
sudo sh -c 'echo -e "[yamcs]\nname=Yamcs\nbaseurl=https://nexus.spaceapplications.com/repository/yamcs/rpm/stable/x86_64\nenabled=1\ngpgcheck=1\ngpgkey=https://nexus.spaceapplications.com/repository/yamcs/keys/yamcs.asc" > /etc/yum.repos.d/yamcs.repo'
```

#### RPM (SLE, openSUSE)

Packages suitable for x86_64 are available via a zypper repository. The repository and key can be installed with the following script:

```shell
sudo rpm --import https://nexus.spaceapplications.com/repository/yamcs/keys/yamcs.asc
sudo sh -c 'echo -e "[yamcs]\nname=Yamcs\nbaseurl=https://nexus.spaceapplications.com/repository/yamcs/rpm/stable/x86_64\nenabled=1\ngpgcheck=1\ngpgkey=https://nexus.spaceapplications.com/repository/yamcs/keys/yamcs.asc" > /etc/zypp/repos.d/yamcs.repo'
```
