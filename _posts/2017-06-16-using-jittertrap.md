---
layout: post
title:  "Using Jittertrap to Detect Traffic"
date:   2017-06-16 14:03:33 -0600
categories: jekyll update
---

[Jittertrap](https://github.com/acooks/jittertrap), a useful open source network analysis tool written in C, has quite a few applications.  After installing Jittertrap from source (note: I needed
to first install libpcacp-dev through apt) I was able to analyze my home networks traffic pretty easily.
<br>
![Image](http://i.imgur.com/hsw2yRv.png)
<br>
On the "front page" of Jittertrap's web UI, you can monitor the TX/RX bitrates of any nic on your machine.  You can also change the time interval of the charts
(you can go as low as 1 millisecond).
<br>
More importantly, Jittertrap can show you the talk distribution of the incoming traffic on your network.
<br>
![Image](http://i.imgur.com/1q05OOQ.png)
<br>
Below the chart, you can see every IP and corresponding port communicating with your machine (I left this blank for obvious reasons).  This is useful because it allows you to see
everything that is happening on your network in a raw form: no hostnames, just straight IP addresses.  You could easily find suspicious (or malicious) traffic using this tool.  You could also
get an idea of how demanding a commonly used service is on your own bandwith.
<br>
Jittertap also has tools for setting triggers and network traps (hence the name).  Basically, you can set alerts for when certain bandwith restrictions are exceeded.  Sysadmins could use this to keep an eye on
bandwith limits and overall traffic.

