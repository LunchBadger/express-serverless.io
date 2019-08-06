---
title: ESP vs AWS Lambda
menuTitle: ESP vs AWS Lambda
description: Find out the truth about using AWS Lambda and why resilient microservices platforms like Express Serverless Platform running on AWS is a better option for both developers and operations.
weight: 1
author: Al Tsang
type: post
date: 2018-11-29T01:08:42+00:00
url: /add-resource/microservices-platform-comparison-express-serverless-on-aws-vs-lambda/
image: /uploads/2018/11/Copy-of-Copy-of-API-Management-32F3-1.png
um_content_restriction:
  - 'a:8:{s:26:"_um_custom_access_settings";s:1:"0";s:14:"_um_accessible";s:1:"0";s:19:"_um_noaccess_action";s:1:"0";s:30:"_um_restrict_by_custom_message";s:1:"0";s:27:"_um_restrict_custom_message";s:0:"";s:19:"_um_access_redirect";s:1:"0";s:23:"_um_access_redirect_url";s:0:"";s:28:"_um_access_hide_from_queries";s:1:"0";}'
classic-editor-remember:
  - classic-editor
categories:
  - Featured
  - Technology
tags:
  - Amazon API Gateway
  - Amazon Web Services Pricing
  - Amiram Shachar
  - api gateway
  - AWS Lambda
  - Developers
  - DevOps
  - Functions as a Service
  - Lambda
  - No-Ops
  - On Premise Serverless Solutions

---
## <span style="font-weight: 400;">Developer Challenges of Serverless and AWS</span>

<span style="font-weight: 400;">AWS pioneered the idea behind serverless when they introduced AWS Lambda: focus on your business logic down to its atomic parts of your applications—</span>**functions**<span style="font-weight: 400;">—and let them worry about the rest. This whole idea eventually led to the <a href="https://go.forrester.com/blogs/11-02-07-i_dont_want_devops_i_want_noops/">NoOps</a> movement.</span>

&nbsp;

<span style="font-weight: 400;">Serverless is a great idea!  It&#8217;s a new paradigm that can be applied to how modern applications are developed and run in the cloud to drastically increase developer focus and productivity.</span>

&nbsp;

<span style="font-weight: 400;">But there are challenges and even &#8220;gotchas&#8221;…</span>

&nbsp;

<li style="font-weight: 400;">
  <b>kitchen sink</b><span style="font-weight: 400;"> &#8211; As with any new technology, developers want to utilize it for every use case imaginable. We call this “shiny object syndrome,” and this leads to a lot of misunderstanding of best practices for when to use serverless functions</span>
</li>
<li style="font-weight: 400;">
  <b>killer latency</b><span style="font-weight: 400;"> &#8211; There’s a cost to spinning up and spinning down the underlying containers that run serverless functions. This latency can be very prohibitive, depending on your use case.<br /> </span>
</li>
<li style="font-weight: 400;">
  <b>vendor lock-in</b><span style="font-weight: 400;"> &#8211; Relying on a single cloud provider&#8217;s serverless solution means investing a lot of time and money in a technology that isn&#8217;t portable should your needs change in the future.</span>
</li>
<li style="font-weight: 400;">
  <b>no on-premises equivalent</b><span style="font-weight: 400;"> &#8211; While several attempts have been made to bring serverless to the on-premises data center, they are often cumbersome, difficult to maintain, and incompatible with cloud-based solutions.</span>
</li>
<li style="font-weight: 400;">
  <b>per-cloud duplication</b><span style="font-weight: 400;"> &#8211; Even if you find a way to adopt multiple serverless implementations, it&#8217;s at the cost of non-uniformity and duplication</span>
</li>

## <span style="font-weight: 400;">Truth About The Costs And Pricing Behind AWS Lambda and Amazon API Gateway</span>

<span style="font-weight: 400;">When you start with two completely different products and try to integrate them together, you’re often left with a diluted experience and a compromise on functionality.  </span>

&nbsp;

_<span style="font-weight: 400;">That’s exactly the case for AWS Lambda and Amazon API Gateway.</span>_

&nbsp;

<span style="font-weight: 400;">If you want to trigger AWS Lambda functions from HTTP requests, AWS forces you to use Amazon API Gateway, a consideration and constraint for all Web-based use cases.</span>

&nbsp;

<span style="font-weight: 400;">The real cost of utilizing AWS Lambda for Web-based use cases is not AWS Lambda itself; it’s exposing Lambda functions through Amazon API Gateway. </span>

&nbsp;

<span style="font-weight: 400;">A lot of articles have been written about this and other challenges utilizing Lambda. Here are a few&#8230;</span>

&nbsp;

<li style="font-weight: 400;">
  <a href="https://medium.com/@amiram_26122/the-hidden-costs-of-serverless-6ced7844780b"><span style="font-weight: 400;">Amiram Shachar’s Medium article</span></a>
</li>
<li style="font-weight: 400;">
  <a href="https://cloudncode.blog/2018/03/22/is-aws-lambda-expensive-to-run/"><span style="font-weight: 400;">Sumit Maingi’s traffic cost analysis of serverless</span></a>
</li>
<li style="font-weight: 400;">
  <a href="https://blog.viacom.tech/2017/03/27/aws-lambda-vs-amazon-ec2-a-discussion-of-lambdas-hidden-costs/"><span style="font-weight: 400;">Viacom’s Lambda cost and functionality tradeoffs</span></a>
</li>

&nbsp;

## <span style="font-weight: 400;">High Performance Experience, Same AWS.</span>

<span style="font-weight: 400;">We saw these challenges and worked with companies that either wanted a better experience or needed a true multi-cloud solution. </span>

&nbsp;

<span style="font-weight: 400;">We took the idea behind serverless and ran with it by providing a seamless experience on top of AWS with Express Serverless Platform.  </span>

&nbsp;

<span style="font-weight: 400;">It gives developers a better way to write and orchestrate serverless functions. It eliminates hidden costs and gives complete control of API Management with a much better API gateway experience.</span>

&nbsp;

<span style="font-weight: 400;">The adoption of Express Serverless Platform means you can also fulfill a hybrid or multi-cloud strategy by writing functions once and running them anywhere, including your own data center, with the same efficiency and experience.</span>

&nbsp;

We&#8217;ve written a complete guide towards understanding the major differences and similarities between Express Serverless Platform on AWS versus AWS Lambda across multiple dimensions, including features and pricing, which is available for download, 
from our <a href="/resource/pdf-guides/" target="_blank">Resources page.</a>

&nbsp;

## <span style="font-weight: 400;">How Express Serverless Platform Lets Developers Have Their Serverless and Kubernetes Cake and Eat it Too</span>

&nbsp;<figure class="post-image">

<img class="aligncenter size-full wp-image-6174" src="/wp-content/uploads/2018/12/ESPonAWS_diagram.png" alt="Express Serverless Platform on AWS"  /></figure> 

&nbsp;

<span style="font-weight: 400;">Express Serverless Platform installs and runs on your AWS account in Kubernetes. You don’t have to manage Kubernetes, because EKS on AWS does that for you.</span>

&nbsp;

The installer provisions a Kubernetes cluster on EKS.  Once Kubernetes is up and running, <span style="font-weight: 400;">Express Serverless Platform</span> is installed into Kubernetes through Helm.

&nbsp;

The following components are deployed as microservices running in Kubernetes pods through <span style="font-weight: 400;">Express Serverless Platform</span>:

&nbsp;

  * model functions
  * serverless functions
  * integrations (connectors)
  * API Gateways

&nbsp;

<span style="font-weight: 400;">Express Serverless Platform is the only platform that seamlessly let’s you write functions and run them in public cloud infrastructure or opt to use long-running containers in a managed Kubernetes cluster.</span>

&nbsp;

<span style="font-weight: 400;">Instead of being forced to wire up AWS Lambda functions to Amazon API Gateway, you can wire them up to <a href="https://express-gateway.io">Express Gateway</a> and have a much better starting point with built-in policies and enterprise features out-of-the-box.  </span>

&nbsp;

This short video shows you exactly how Express Serverless Platform runs on AWS.

&nbsp;

<p style="text-align: center;">
  <iframe src="https://player.vimeo.com/video/307326666" width="640" height="360" frameborder="0" allowfullscreen="allowfullscreen"></iframe>
</p>

&nbsp;

Hope you found this post beneficial. Don&#8217;t forget to download the <a href="/resource/pdf-guides/" target="_blank">AWS Lambda versus Express Serverless Platform on AWS comparison guide.</a> 


&nbsp;

And if you&#8217;re interested in more of these topics, join the live discussion on Twitter **[@lunchbadger][1]** or **[@express_gateway.][2]**

&nbsp;
&nbsp;

{{% button href="https://facebook.com/sharer/sharer.php?u=https%3A%2F%2Fexpress-serverless.io%2Fresource%2Fmicroservices-platform-comparison-express-serverless-on-aws-vs-lambda%2F" icon="fab fa-facebook" %}}Share{{% /button %}}

{{% button href="https://twitter.com/intent/tweet/?text=ESP%20vs%20AWS%20Lambda&amp;url=https%3A%2F%2Fexpress-serverless.io%2Fresource%2Fmicroservices-platform-comparison-express-serverless-on-aws-vs-lambda%2F" icon="fab fa-twitter" %}}Tweet{{% /button %}}

{{% button href="https://www.linkedin.com/shareArticle?mini=true&amp;url=https%3A%2F%2Fexpress-serverless.io%2Fresource%2Fmicroservices-platform-comparison-express-serverless-on-aws-vs-lambda%2F&amp;title=ESP%20vs%20AWS%20Lambda&amp;summary=ESP%20vs%20AWS%20Lambda&amp;source=https%3A%2F%2Fexpress-serverless.io%2Fresource%2Fmicroservices-platform-comparison-express-serverless-on-aws-vs-lambda%2F" icon="fab fa-linkedin" %}}Link{{% /button %}}





 [1]: http://www.twitter.com/lunchbadger
 [2]: https://twitter.com/express_gateway