---
title: 'API Gateways Comparison: Features & Pricing of Kong vs. Express Gateway'
author: Al Tsang
menuTitle: Kong vs EG
type: post
date: 2018-01-30T14:10:49+00:00
url: /blog/compare-kong-api-gateway-express-features/
image: /uploads/2018/01/Multi-Cloud-Kubernetes-and-Our-New-Partnership-with-Joyent-35.png
um_content_restriction:
  - 'a:8:{s:26:"_um_custom_access_settings";s:1:"0";s:14:"_um_accessible";s:1:"0";s:19:"_um_noaccess_action";s:1:"0";s:30:"_um_restrict_by_custom_message";s:1:"0";s:27:"_um_restrict_custom_message";s:0:"";s:19:"_um_access_redirect";s:1:"0";s:23:"_um_access_redirect_url";s:0:"";s:28:"_um_access_hide_from_queries";s:1:"0";}'
categories:
  - Technology
tags:
  - Administration of Kong API Gateway
  - Compare open source API Gateway
  - Express API Gateway
  - express.js
  - How does Kong compare to
  - Kong API Gateway
  - microservices
  - What is an API Gateway?

---
# <img class="aligncenter size-full wp-image-3296" src="/wp-content/uploads/2018/01/Multi-Cloud-Kubernetes-and-Our-New-Partnership-with-Joyent-35.png" alt="Compare: Kong API gateway versus Express Gateway" width="1024" height="512" srcset="/wp-content/uploads/2018/01/Multi-Cloud-Kubernetes-and-Our-New-Partnership-with-Joyent-35.png 1024w, /wp-content/uploads/2018/01/Multi-Cloud-Kubernetes-and-Our-New-Partnership-with-Joyent-35-300x150.png 300w, /wp-content/uploads/2018/01/Multi-Cloud-Kubernetes-and-Our-New-Partnership-with-Joyent-35-768x384.png 768w, /wp-content/uploads/2018/01/Multi-Cloud-Kubernetes-and-Our-New-Partnership-with-Joyent-35-225x113.png 225w, /wp-content/uploads/2018/01/Multi-Cloud-Kubernetes-and-Our-New-Partnership-with-Joyent-35-512x256.png 512w" sizes="(max-width: 1024px) 100vw, 1024px" />

# <span style="font-weight: 400;">Kong API Gateway VS. Express Gateway</span>

Two popular open source projects &#8211; two very different approaches. We&#8217;ve gotten a lot of questions about what to look for in an API Gateway, what is an API Gateway and even how an API gateway fits into your Microservices architecture. So, let&#8217;s take a deeper look at all of this and more as we break down the differences (and similarities) of the most popular projects for the API Gateway use case.

In this tear down format, we&#8217;ve got** [Kong API Gateway][1]** and we&#8217;re going to compare it to[ **Express Gateway,**][2] an open source API Gateway built entirely on Express.js.

&nbsp;

[_Download the detailed guide here._][3]

&nbsp;

Not ready? Let&#8217;s kick things off then with a quick hype-free run down. Buzzword vortex is not our style, so we asked our community of developers and executives what the real deal was all about and here&#8217;s a summary based on their real-time use cases, issues and solutions.

## Overview

<span style="font-weight: 400;">Kong has a compelling story around performance and reliability because it is built on top of NGINX and we love NGINX. However; we&#8217;ve come across some dependencies that can slow you down or make it more difficult to ship.</span>

&nbsp;

<span style="font-weight: 400;">What&#8217;s Lua? Well, we were asking ourselves the same thing because custom plugins for Kong must be written in Lua. In the recent <a href="https://insights.stackoverflow.com/survey/2017">2017 Developer Survey by Stack Overflow</a>, they listed popular technologies&#8230;and only 2.8% of developers surveyed used Lua. With professional developers, it was even lower at 2.3%.</span>

&nbsp;

_<span style="font-weight: 400;">That&#8217;s a bummer. </span>_

&nbsp;

<span style="font-weight: 400;">Express Gateway is also open source API Gateway, but it&#8217;s built on <a href="https://expressjs.com/">Express.js</a>, a minimal and flexible Node.js web application framework. Custom plugins are written in JavaScript (<a href="https://insights.stackoverflow.com/survey/2017">the number 1 result among the surveyed developers</a>).  In an era of speed and agility, we thought this was an especially poignant aspect to the way Express Gateway is built. </span>

## Factors to consider when comparing API Gateways

  * **Elevator Pitches** &#8211; What does it do in 3 sentences or less (ok maybe a bit more than that).
  * **Features and Architecture** &#8211; What&#8217;s under the hood with Kong API Gateway and Express Gateway?
  * **Getting Started, Deployment and Configuration** &#8211; Are we up yet?
  * **Database Support** &#8211; What is it and where to find it.
  * **Administration and Maintenance** &#8211; How to maintain it, resource allocation and more
  * **Built-in Plugin Support** &#8211; No frills, side-by-side comparison of popular features of Kong API Gateway and Express Gateway
  * **Custom Plugin Support** &#8211; What else can we add
  * **Enterprise Versions **&#8211; Both Kong and Express Gateway have enterprise versions &#8211; what are the key differences?
  * + much more&#8230;

## Why are we talking API Gateways?

In our analysis, we&#8217;ll compare the Kong API Gateway and Express Gateway, an API Gateway built entirely on Express.js. We&#8217;ll also explain exactly what an API Gateway is so that it puts it all into context. This interesting piece of architecture is important if you are working with APIs and Microservices. Even if you&#8217;re just working on the strategy side, do not under estimate the flexibility and agility that comes from using API Gateways.

&nbsp;

_TLDR: API Gateways data where it needs to go in a secure, orderly fashion._

&nbsp;

So even if you think you&#8217;ve got it all locked and loaded, it never hurts to take a look at what a little open source can do for your business or tech stack.

&nbsp;

<div class="spaced" style="padding-top:15px; clear:both;" >
</div>

<h1 style="text-align: center;">
  <a href="/resource/pdf-guides/"  class="btn button center cta">Get The Deep Dive</a>
</h1>

<div class="spaced" style="padding-top:15px; clear:both;" >
</div>

## Moving On

&nbsp;

If you&#8217;ve got questions about this comparison or analysis, let us know. If you&#8217;re interested in how to migrate from Kong or even just to give Express Gateway a try, hit us up. We&#8217;re always on the hunt for use cases and understanding more about what companies are using, issues they&#8217;re facing or successes they&#8217;ve felt.

&nbsp;

Additionally, if you&#8217;re interested in more of these topics, join the live discussion on twitter **([@lunchbadger][5])** or (**[@express_gateway).][6]**



 [1]: https://getkong.org/
 [2]: http://www.express-gateway.io?utm_source=Comparison_LP_Kong&utm_medium=blog&utm_campaign=2018-10-comparisons&utm_content=link
 [3]: /resource/pdf-guides/ 
 [4]: https://www.lunchbadger.com/enterprise/
 [5]: http://www.twitter.com/lunchbadger
 [6]: https://twitter.com/express_gateway