---
layout: post
title:  "Deploying Go Revel Web Apps on OpenShift"
date:   2017-11-07 16:24:40 -0600
categories: jekyll update
---

Recently, I wrote a [web app](https://github.com/sgreene570/ballots) in Golang using the Revel framework that automatically creates vote ballots for [CSH](https://csh.rit.edu) through the GitHub API.
After learning Flask, I felt that branching out into a new web frameworks couldn't hurt.  Turns out, the only difficult part of working with Revel was trying to deploy
my code on [OpenShift](https://www.openshift.com/).

OpenShift uses the Source-to-Image (s2i) framework to create runtime containers for individual applications.  At the moment,
the Go s2i docker image does not support Revel projects as this docker image compiles source code with the base Go compiler.
Revel projects need to be compiled with the Revel executable to ensure that all assets are properly
linked.  Once a Revel project is compiled, the webserver can be started by running the`run.sh`script in the Revel build directory.

![Image](https://i.imgur.com/RQCQfgt.png)

I decided to fork the [s2i-go docker image repo](https://github.com/openshift-s2i/s2i-go) to create a Revel specific s2i
image.  This was my first time ever looking at docker image source code, so modifying the image's build script took some time. Now, I have a working
[s2i-revel container](https://github.com/sgreene570/s2i-revel/blob/master/s2i/assemble) that reliably deploys Revel projects.
