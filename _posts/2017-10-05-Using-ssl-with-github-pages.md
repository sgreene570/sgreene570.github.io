---
layout: post
title:  "Using SSL With GitHub Pages and a Custom Domain"
date:   2017-10-05 10:30:06 -0600
categories: jekyll update
---

GitHub pages is encrypted over https if you connect using GitHub's DNS (for example, using sgreene570.github.io to connect to this blog instead of stevegreene.me).
However, if you use your own domain name for your GitHub pages site, GitHub will not provice SSL certificates for you given the complexity of
working with external DNS providers.  Instead, you can use Cloudflare to force https connections to your GitHub pages site, like I am.
If you already have your DNS provider configured for your GitHub pages, Cloudflare will most likely auto detect your redirects when you create your free acocunt.
This means all you have to do to use Cloudflare with your Github pages site is change your domain providers nameserver to Cloudflare's nameserver.
If you do not have your domain routed to GitHub already, Cloudflare can do this under the DNS section (just create an A record to point
to GitHub IP space specified in your settings of your GitHub pages repo).

If you are using Namecheap domain hosting, all you have to do to switch to Cloudflare is change the namerserver section under your
domain management page to look similair to mine:

![Image](https://i.imgur.com/f0wJQYz.png)

Next, go to the Crypto section in Cloudflare and select the "Alawys use https" option to force redirect all traffic to use SSL.
Now, when readers connect to your site using http, Cloudflare will automatically redirect them to your site with SSL enabled.
Given that Cloudflare offers this service for free, there is no reason not to encrypt your site traffic, especially if you have any sort
of form input on your site.
