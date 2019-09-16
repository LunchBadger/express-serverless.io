---
title: The Ultimate IoT Backend using Node.js, Serverless and Kubernetes
menuTitle: The Ultimate IoT Backend
author: Al Tsang
type: post
date: 2017-10-11T16:21:32+00:00
url: /blog/ultimate-iot-backend-using-node-js-serverless-kubernetes/
featured_image: /uploads/2017/10/ultimate-iot-backend.png
categories:
  - Technology
tags:
  - api
  - API Design
  - API Management
  - APIs
  - Build an IoT Backend
  - Docker
  - Express Gateway
  - IoT
  - Joyent
  - Node.js

---
<p class="p1">
  In this post, we&#8217;ll cover the components of an IoT backend using Node.js, FaaS (functions-as-a-service or serverless) and Kubernetes to sustainably build a backend to your IoT applications. We&#8217;ll provide new concepts, as well as helpful tips to get you off to a great start.
</p>

## **What is an IoT Backend?** {.p2}

<p class="p1">
  There are a few primary components to constructing the backend of an IoT application.
</p>

<ul class="ul1">
  <li class="li1">
    <b>Data Storage</b> &#8211; <i>You need the right tools to manage your machine data can make the difference between success and failure.</i>
  </li>
  <li>
    <b>Protocols</b> &#8211; <i>Devices or &#8220;things&#8221; communicate through more compact and efficient the payloads We&#8217;re talking about protocol support just as MQTT and CoAP in addition to standard JSON over REST</i><i>.</i>
  </li>
  <li class="li1">
    <b>Analytics</b> &#8211; <i>It&#8217;s not enough to just collect and store data. In order to truly have an impact on your growth trajectory, you need</i> a<i>nalytics to provide valuable insights.</i>
  </li>
  <li class="li1">
    <b>Services</b> &#8211; <i>Next, you need the appropriate services to be able to execute on those insights.</i>
  </li>
</ul>

So, all of these components take expertise to understand. When it comes to stitching them altogether, it can be difficult for enterprise executives and developers to understand where to start.

## **Where do Node.js, Serverless and Kubernetes fit in?** {.p2}

As you begin to think about how to design your backend, you need to consider different aspects of your API Strategy. Specifically, what languages can you use (such a Node.js) that will help you hire quickly or maintain a flexible and productive development environment. For developers, choosing a Runtime may not seem important, but Docker and Kubernetes make your Runtime portable because every cloud provider supports containers.  In addition, Serverless provides a layer of ease of use and productivity.

So even if you&#8217;re just focused on Microservices integration and composition, you can still achieve seamless API and Microservices development.

## API Growth Strategies Start With API Management

_As you already know, API Management is a [key growth strategy for Enterprise companies and developers alike.][1]_

In our example, we have used Node.js, Docker and Serverless runtime as a powerful combination within the LunchBadger platform. Even though we are using this to build an Backend for our IoT application, it works for a broad spectrum of use cases.

If you have already been on the LunchBadger platform, you&#8217;ll notice that there&#8217;s a brand new box in the GUI. _**(We&#8217;ll have more on that in the upcoming weeks!)**_

## Express Gateway as the API Gateway Solution

An API Gateway Solution is just one last piece to the puzzle. By now, you will have heard of our open source project, [Express Gateway][2].  As cosponsors of Express Gateway, we&#8217;re partnering with Joyent and the Node.js developer community to provide an open source API Gateway built entirely on Express.js.

Together, we provide a s_imple, flexible and community driven open source tool that can be used anywhere by anyone._

The API Gateway is at the heart of Microservices which means it will continue to play an important part in your IoT Backend. We are keeping Express Gateway open source because we believe that developers deserve next generation tooling. When you pair this project with an infrastructure platform like LunchBadger which supports the management and composition of your microservices, you can get started in minutes &#8211; not hours or days.

## Think Function As A Service

If you have never heard of this term before, get with the program!

> **Function as a service** (FaaS) describes a category of cloud computing **services** which are a platform. This platform allows customers to run, develop and manage application functionalities without having to build or maintain the infrastructure.

Instead of having to maintain all of your own infrastructure, you can leverage a platform to do it for you? Seems pretty simple. However; it&#8217;s very powerful and can help you add some velocity to your development cycles.

## Key Takeaways

Express Gateway gives you API gateway capabilities while LunchBadger gives you composition and aggregation/mashup for rolling up fine grain microservices into engagement level APIs.

In the next week, we&#8217;ll share a live demo on our latest concepts.

  * How to pull together Serverless, Docker/Kubernetes (Runtime) and an open source API gateway into an easy to use platform
  * How to conserve resources at the Enterprise level to maximize productivity
  * and more ideas on how to pilot this within your company.

If you&#8217;ve been looking for a deep dive into LunchBadger&#8217;s capabilities and ease of use or just protips on how to execute your API Strategy &#8211; stay tuned for more!

## Moving On

Next week, we&#8217;re headed to the [Samsung Developer&#8217;s Conference][3] to make some noise with the co-sponsor of [Express Gateway][2], Joyent. Building IoT applications is hard enough, building a sustainable backend infrastructure shouldn&#8217;t be.

So we&#8217;ve chosen the Samsung Developer&#8217;s conference as a way to make this important aspect of your tech stack easier, more flexible and with a little love from open source tools like [Express Gateway][2], an open source API gateway built entirely on Express.js.

Additionally, if you&#8217;re interested in more of these topics, join the live discussion on twitter **([@lunchbadger][4])** or (**[@express_gateway).][5]**

If you have questions about Express Gateway or want to get more involved in our community, please [consider joining our Gitter][6]. We&#8217;ve been working hard to create an open and transparent environment where you can get your questions answered and meet other devs interested in open source.

* * *

  * [Get Started With Express Serverless Platform][8] &#8211; your feedback helps prioritize our roadmap with the most value realized within the shortest amount of time
  * Learn about the [inaugural feature set][9] we’re striving for to make APIs repeatedly fast, easy and manageable as you evolve through the API lifecycle itself.
  * Check out our Open Source Initiative: [The Express Gateway][2]

 [1]: https://www.lunchbadger.com/api-strategies-in-the-enterprise/
 [2]: http://www.express-gateway.io
 [3]: https://www.sdc2017.com/program/session-catalog/
 [4]: http://www.twitter.com/lunchbadger
 [5]: https://twitter.com/express_gateway
 [6]: https://gitter.im/ExpressGateway/express-gateway
 [7]: http://eepurl.com/cSR5vT
 [8]: https://www.express-serverless.io/getting-started/
 [9]: https://www.express-serverless.io/