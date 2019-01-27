---
layout: post
title:  "homelab - squid proxy"
date:  2019-01-27
categories: homelab
---

I am going to start writing more about some of the stuff that I build in my
homelab. So with the first post of 2019 here is a post about the latest vm, a
squid proxy.

I use centos 7 as a template for most of the virtual machines I make. I work with centos
because its the most comfortable for me, and using rpm, yum, and dnf as the package
managers is straight forward. It really does not make a difference though to me personally. I just
want to be able to spin vms up quick and I am most familiar with this type
of os from my days working in system administration at various web hosts.

Squid was always something that I wanted to setup but have never done before,
so I started light and just configured a basic proxy. Here are the links to the
files so if you want a basic libvirtd based squid setup, this can be used. You
may have to modify the Vagrantfile slightly if you want to use virtualbox or
not use a bridge as a second network interface. I leave that to you. Proxy all
the HTTP connections for science. 

Also, for a fun bonus read that inspired me to read up and learn more about
squid in particular is this really interesting write-up by Anthony Ferrara on how he hacked stackoverflow. I won't spoil how he gains admin acces 
That writeup can be read [here](https://blog.ircmaxell.com/2012/11/anatomy-of-attack-how-i-hacked.html). 

Code for vagrant vm:[centos_squid_proxy](https://git.mcdevitt.tech/bpmcdevitt/homelab_scripts/tree/master/vagrant/centos_squid_proxy)
