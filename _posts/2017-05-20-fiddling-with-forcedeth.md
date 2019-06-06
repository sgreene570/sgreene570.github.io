---
layout: post
title:  "Using the Nvidia mc61 Ethernet Controller with Debian"
date:   2017-05-20 16:16:01 -0600
categories: jekyll update
---

Sadly, my desktop motherboard has an outdated chipset.  For ethernet, I am left
with a Nvidia mc61 gigabit controller, which is hardly supported and very
sticky with any flavor of linux.  After trying to debug my connection issues through network manager
(a strategy that almost always works), I was still unable to get my onboard ethernet controller working.  At first,
google searches suggested adding a few driver related lines to my grub config,
which ultimately led me nowhere.  After more research, I found the [Nvidia
forcedeth module](https://github.com/torvalds/linux/blob/master/drivers/net/ethernet/nvidia/forcedeth.c)
in the modules directory of my OS.  As it turns out,
changing the launch time parameters of the forcedeth module is a common fix for
several of nividia's old onboard ethernet cards.  After digging through lots of
forum posts about the mc61 and the mc55 ethernet cards, I finally found what parameters the forcedeth module
needed to be launched with.
<br>
To enable Nvidia mc61 in Debian:
<br>
create the file`/etc/modprobe.d/forcedeth.conf`
<br>
and add to it:`options forcedeth msi=0 msix=0`
<br>
While digging around for these two variable assignments did take
a while, I did learn a lot about how the kernel handles drivers.  Also,
reading through the forcedeth source code was a fun exercise that I would highly
recommend to anyone with some knowledge of the C language.  As someone who has mostly dealth with
C as a generic programming language rather than a hardware programming language, I find it really interesting
to read through hardware firmware.
