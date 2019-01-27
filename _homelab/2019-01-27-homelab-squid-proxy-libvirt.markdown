---
layout: homelab
title:  "homelab - squid proxy"
date:  2019-01-27
categories: homelab
---

It is a new year. Time to start writing more about some of the stuff that I build in my
homelab. So with the first post of 2019, here is a post about the latest virtual machine I deployed, a squid proxy server. I can use this for security testing web applications.

Centos 7 is used as template for most of the virtual machines I make. This is because it's the most comfortable for me, and using `rpm, yum` and `dnf` as the package
managers is straight forward. It really does not make a difference though to me personally. I just want to be able to spin vms up quick and I am most familiar with this type of os from my days working in system administration at various web hosts.

Squid has always been something that I wanted to setup but have never gotten around to.
So I started very basic and lightweight. The default configuration with squid is there to set you up with an unauthenticated proxy that listens locally on the network. Here are the links to the files. These are currently for a libvirt based setup. You will have to modify the `Vagrantfile` slightly if you want to use virtualbox or
not use a bridge as a second network interface. Also feel free to modify the resources suited to your homelabs resource limitations (cpus/ram). I leave that to you. Proxy all
the HTTP connections, for science!

Also, for a fun bonus read that inspired me to read up and learn more about
squid in particular is this really interesting write-up by Anthony Ferrara on how he hacked stackoverflow. Also some very good info on the `X-Forwarded-For` http header. I won't spoil how he gains admin access. Here is a [link](https://blog.ircmaxell.com/2012/11/anatomy-of-attack-how-i-hacked.html) to the writeup.
* Code - [centos_squid_proxy](https://git.mcdevitt.tech/bpmcdevitt/homelab_scripts/tree/master/vagrant/centos_squid_proxy)
* Squid - <http://www.squid-cache.org/Doc>
* Vagrant - <https://www.vagrantup.com>
* X-Forwaded-For <https://en.wikipedia.org/wiki/X-Forwarded-For>

Shellscript to install squid in CentOS 7 (nice and simple):
```bash
#!/usr/bin/env bash
# update yum
sudo yum update -y

# install and enable squid proxy
sudo yum -y install squid

sudo systemctl start squid
sudo systemctl enable squid
sudo systemctl status squid

# give us ifconfig and vim
sudo yum install net-tools vim -y

ip_address=$(ip address show eth1 | grep 'inet ' | sed -e 's/^.*inet //' -e 's/\/.*$//')
port='3128'

echo "Proxy Info:"
echo "--------------------------------------"
echo "http info: http://$ip_address:$port"
echo "--------------------------------------"
```
