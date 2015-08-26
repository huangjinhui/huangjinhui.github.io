---
layout: post
title: "How to configure network in virtualboxed centos 7"
description: ""
category: linux
tags: [centos]
---
{% include JB/setup %}

Host: ubuntu 14.04
virtualbox 5.02
Guest: centos 7

**what i want:** under host machine, connect guest using ssh.

During the installation, i've only configured the guest machine's network setting to share the internet access with the host machine, using NAT.

![](images/2015-08-26-centos-network-conf1.png)

Now we need to do is to create a virtual network adapter in virtualbox's networking settings.

![](images/2015-08-26-host-only.png)

and turn the created virtual network adapter in guest machine on.

![](images/2015-08-26-19:26:05-network-setting.png)

by default, the ip address of the virtual adapter _vboxnet0_ is `192.168.56.101`, so now we should be able to ssh to the guest machine.

![](images/2015-08-26-20:28:57-ssh-login.png)

any questions? :)
