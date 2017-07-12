---
layout: post
title:  "Disabling Sleep on Lid Close When Using Systemd to Shutdown"
date:   2017-07-12 12:32:00 -0600
categories: jekyll update
---

Closing your laptop lid is almost second nature after you shut down your computer.
However, if your power down settings are not configured correctly, your laptop may
enter a sleep state mid shutdown (which can be a huge pain).
I have had this happen to me several times with debian before I realized what was really going on.
In order to disable sleeping on lid closes during shutdown, you can modify the systemd
shutdown sequence.  Systemd will run any  scripts placed in the
`/usr/lib/systemd/system-shutdown` directory when shuting down.
For this case, I made the following systemd-shutdown script, called `lidsleep.service`
<br>
`[Unit]`
<br>
`Description=Disable lid closure sleep when powering off`
<br>
`Before=shutdown.target`
<br>
<br>
`[Service]`
<br>
`type=oneshot`
<br>
`RemainAfterExit=true`
<br>
`ExecStart=/bin/true`
<br>
`ExecStop=systemd-inhibit --what=handle-lid-switch sleep 1d`
<br>
<br>
`[Install]`
<br>
`WantedBy=multi-user.target`
<br>
This script uses the `systemd-inhibit` command to temporarily disable lid activated sleeping.  Once the system has been fully powered down,
the systemd block will no longer be applicable until the next shutdown.
