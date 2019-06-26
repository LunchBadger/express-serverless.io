---
title: API Gateway Comparison – Features and Pricing of Amazon AWS API Gateway and Express Gateway
author: Al Tsang
menuTitle: AWS API Gateway vs EG
type: post
date: 2018-01-23T13:30:58+00:00
url: /blog/compare-amazon-aws-api-gateway-express-features/
image: /uploads/2018/01/Multi-Cloud-Kubernetes-and-Our-New-Partnership-with-Joyent-27.png
um_content_restriction:
  - 'a:8:{s:26:"_um_custom_access_settings";s:1:"0";s:14:"_um_accessible";s:1:"0";s:19:"_um_noaccess_action";s:1:"0";s:30:"_um_restrict_by_custom_message";s:1:"0";s:27:"_um_restrict_custom_message";s:0:"";s:19:"_um_access_redirect";s:1:"0";s:23:"_um_access_redirect_url";s:0:"";s:28:"_um_access_hide_from_queries";s:1:"0";}'
categories:
  - Announcement
  - Technology
tags:
  - Administration and Maintenance of AWS API Gateway
  - Amazon API Gateway
  - AWS API Gateway
  - Express API Gateway
  - express.js
  - How does AWS compare to
  - microservices
  - What is an API Gateway?

---
# <img class="aligncenter size-full wp-image-3202" src="/wp-content/uploads/2018/01/Multi-Cloud-Kubernetes-and-Our-New-Partnership-with-Joyent-27.png" alt="Express Gateway vs. Amazon API Gateway" width="1024" height="512" srcset="/wp-content/uploads/2018/01/Multi-Cloud-Kubernetes-and-Our-New-Partnership-with-Joyent-27.png 1024w, /wp-content/uploads/2018/01/Multi-Cloud-Kubernetes-and-Our-New-Partnership-with-Joyent-27-300x150.png 300w, /wp-content/uploads/2018/01/Multi-Cloud-Kubernetes-and-Our-New-Partnership-with-Joyent-27-768x384.png 768w, /wp-content/uploads/2018/01/Multi-Cloud-Kubernetes-and-Our-New-Partnership-with-Joyent-27-225x113.png 225w, /wp-content/uploads/2018/01/Multi-Cloud-Kubernetes-and-Our-New-Partnership-with-Joyent-27-512x256.png 512w" sizes="(max-width: 1024px) 100vw, 1024px" />

# <span style="font-weight: 400;">Amazon API Gateway VS. Express Gateway</span>

If you&#8217;re curious about how your API Gateway stacks up, now&#8217;s the time to listen up because we&#8217;re breaking down the differences (and similarities) of the most popular projects for the API Gateway use case.

First up, we&#8217;ve got **<a href="https://aws.amazon.com/api-gateway/" target="_blank" rel="noopener noreferrer">Amazon API Gateway</a>** and we&#8217;re going to compare it to[ **Express Gateway,**][1] an open source API Gateway built entirely on Express.js.

&nbsp;

_TLDR: You can [skip ahead to the deep dive.][2]_

&nbsp;

For the rest of you, here&#8217;s a quick hype-free run down. If you&#8217;re like us and sick of the buzzword salad, then take a look at the real deal and let us know what you think.

## Overview

While it&#8217;s true that Amazon (AWS) is ubiquitous across most use cases, it&#8217;s important to remember that it may not be right for everything. _What do you do?_ That&#8217;s the problem &#8211;** vendor lock in**. Being locked into a vendor costs you money, but more importantly, it costs you time. Think of agility and speed as two of your best tools to be able to respond to the needs of customers or demands of the market. Amazon API Gateway is low level. If you want features like identity, authentication and authorization that other API gateways have natively &#8211; guess what? You&#8217;re looking at yet another proprietary offering like AWS Cognito OR coding everything yourself in a custom authorizer or in AWS Lambda &#8211; from scratch.

&nbsp;

_Speed=Survival_

&nbsp;

Hidden fees and the cost of migration at scale can slow you down. There&#8217;s more &#8220;gotchas&#8221; where that came from. For instance,  Did you know that writing to AWS is part of your free Tier Usage but reading is not. What good does that do? AWS Lambda is low cost so you can catch a break there, but you&#8217;ve got to use the Amazon API Gateway to surface AWS Lambda natively outside of AWS if you want to do so via HTTP.  Check out this <a href="https://medium.com/@amiram_26122/the-hidden-costs-of-serverless-6ced7844780b" target="_blank" rel="noopener noreferrer">Medium article that reveals the real cost of serverless in AWS</a> &#8211; not Lambda &#8211; yep &#8211; Amazon API Gateway.

&nbsp;

_News Flash:_ it&#8217;s **expensive**.

&nbsp;

So while we won&#8217;t cover those aspects in the comparison between Amazon (AWS) API Gateway and Express Gateway, keep this (and more) in mind when looking at Amazon (AWS) API Gateway.

## Factors to consider when comparing API Gateways

  * **Elevator Pitches** &#8211; What&#8217;s the short and sweet?
  * **Features and Architecture** &#8211; How does that backend look?
  * **Getting Started, Deployment and Configuration** &#8211; What does it take to get up and running?
  * **Administration and Maintenance** &#8211; How much effort is it on a daily basis?
  * **Features Comparison** &#8211; Side by Side showdown of popular features you are already using (or should be)
  * **Custom Extensions** &#8211; What does the extension ecosystem look like?
  * + much more&#8230;

## Why are we talking API Gateways?

In our analysis, we&#8217;ll compare the Amazon (AWS) API Gateway and Express Gateway, an API Gateway built entirely on Express.js. We&#8217;ll also explain exactly what an API Gateway s, but for now &#8211; you need to know that this handy piece of architecture is important if you are working with APIs and Microservices. Two things, we&#8217;re obviously passionate about. Think of an API Gateway&#8230;like air traffic control. They get that data where it needs to go so even if you think you&#8217;ve got it locked down, it never hurts to take a look at the latest and greatest (especially if it&#8217;s open source!).

<div class="spaced" style="padding-top:15px; clear:both;" >
</div>

<h1 style="text-align: center;">
  <a href="/resources/comparison-guides/ "  class="btn button center cta">Download the detailed guide here</a>
</h1>

<div class="spaced" style="padding-top:15px; clear:both;" >
</div>

## Moving On

Disclaimer: No actual HoneyBadgers were hurt during this comparison. Additionally, if you&#8217;re interested in more of these topics, join the live discussion on twitter **([@lunchbadger][3])** or (**[@express_gateway).][4]**



 [1]: http://www.express-gateway.io?utm_source=Comparison_LP_AWS&utm_medium=blog&utm_campaign=2018-10-comparisons&utm_content=link
 [2]: /resources/comparison-guides/
 [3]: http://www.twitter.com/lunchbadger
 [4]: https://twitter.com/express_gateway