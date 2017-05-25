---
layout: post
title:  "Fiddling With Forcedeth"
date:   2017-05-20 16:16:01 -0600
categories: jekyll update
---

Sadly, my desktop motherboard has an outdated chipset.  For ethernet, I am left
with the nvidia mc61 gigabit controller, which is hardly supported and very
sticky with any flavor of linix.  After trying the typical network manager debug
route, I was still unable to get ethernet working on my desktop.  At first,
google searches suggested adding a few driver related lines to my grub config,
which ultimately led me nowhere.  After more research, I found the [nvidia
forcedeth module](https://github.com/torvalds/linux/blob/master/drivers/net/ethernet/nvidia/forcedeth.c) 
in the modules directory of my OS.  As it turns out,
changing the launch time parameters of the forcedeth module is a common fix for
several of nividia's old onboard ethernet cards.  After digging through lots of
forum posts about the mc61 and the mc55 ethernet cards, I finally found what
values I needed to change at startup.  By adding "options forcedeth msi=0
msix=0" to /etc/modprobe.d/forcedeth.conf, I was able to use my onboard
ethernet.  While digging around for these two variable assignments certainly
took a while, I did learn a lot about how the kernel handles modules.  Also,
reading through the forcedeth source code was  fun exercise that I would highly
recommend to anyone with some knowledge of the C language.
