---
title: 'API Management Reimagined: Authentication Authorization Audit'
menuTitle: API Management Reimagined
description: For Developers and DevOps engineers, an open source API Gateway and Serverless platform make the three As of API management easy.
author: Al Tsang
type: post
date: 2018-10-16T21:06:48+00:00
url: /blog/api-management-authentication-authorization-audit/
image: /wp-content/uploads/2018/10/1-1.png
um_content_restriction:
  - 'a:8:{s:26:"_um_custom_access_settings";s:1:"0";s:14:"_um_accessible";s:1:"0";s:19:"_um_noaccess_action";s:1:"0";s:30:"_um_restrict_by_custom_message";s:1:"0";s:27:"_um_restrict_custom_message";s:0:"";s:19:"_um_access_redirect";s:1:"0";s:23:"_um_access_redirect_url";s:0:"";s:28:"_um_access_hide_from_queries";s:1:"0";}'
categories:
  - Featured
  - Technology
tags:
  - API Management
  - authentication
  - Authentication with an API Gateways
  - authorization and audit capabilities
  - scalable Kubernetes infrastructure

---
## **Authentication Authorization And Audit: The Operations Perspective**

<span style="font-weight: 400;">API Gateways provide a set of features that enable secure access to its API endpoints. These features fall under three broad categories:</span>

  *  <span style="font-weight: 400;">        <strong>Authentication:</strong> Who is allowed to access the API Gateway at all? (Access Control)</span>
  *  <span style="font-weight: 400;">        <strong>Authorization:</strong> Who is allowed to perform a certain operation using exposed APIs (Permissions / Privileges)</span>
  *  <span style="font-weight: 400;">        <strong>Audit:</strong> Capturing sufficient information for each client request to be able to detect and possibly prevent malicious activity</span>

<span style="font-weight: 400;">An administrator of <em>any API Gateway platform</em> need to be aware of these capabilities, which could be a bit different compared to securing web sites and databases.</span>

&nbsp;

<span style="font-weight: 400;">There are a few important considerations beyond what most administrators typically manage.</span>

&nbsp;

<span style="font-weight: 400;">How can you define microservices and serverless functions and expose them as APIs? </span><span style="font-weight: 400;">What about industry best practices for API Management?</span>

&nbsp;

<span style="font-weight: 400;">Defining microservices and serverless functions and exposing them as APIs is just the beginning and can take time to do it right. For developers, industry standard authentication, authorization and audit capabilities also come at a price: time, scale and resources. It takes an experienced dev to ensure that these practices are followed throughout the entire software development lifecycle. </span>

&nbsp;

## **API Management with Express Serverless Platform**

<span style="font-weight: 400;">Express Serverless Platform is a Microservices and Serverless Platform for APIs. It is unique in that it allows us to design and deploy microservices.</span>

&nbsp;

<span style="font-weight: 400;">The platform allows us to expose both model-based microservices and serverless Functions through REST APIs, using an API Gateway (the open source</span> [<span style="font-weight: 400;">Express Gateway</span>][1]<span style="font-weight: 400;">).</span>

&nbsp;

### How does this help developers and DevOps teams with API Management?

<span style="font-weight: 400;">The Express Serverless Platform is unique in that it brings together tooling to develop microservices, and one-click deployment to a scalable Kubernetes infrastructure. This accelerates development and significantly increases developer productivity. The tooling environment is actually browser-based and known as Canvas.</span>

&nbsp;

<span style="font-weight: 400;">Let&#8217;s  focus some attention on the API Management component, that is, Express Gateway. However, all configurations on Express Gateway, including those relevant for authentication, authorization and audit, can be applied through the Canvas.</span>

&nbsp;

### **Simple and Straight forward AAA Features in Express Gateway**

<span style="font-weight: 400;">Express Gateway supports three industry standard mechanisms for client authentication: basic authentication (username / password), Key-based authentication (using API access Keys) and OAuth2 (for granting access to APIs from third-party applications).</span>

&nbsp;

<span style="font-weight: 400;">Authorization mechanism in Express Gateway is simple and innovative. For each API endpoint, the administrator can specify one or more scope(s). A scope is just like a tag indicating the type of users / applications that may need access to this API endpoint. Correspondingly, users granted access to the API gateway may be assigned one or more scopes. A user can retrieve information from an API only if she is assigned a matching scope.</span>

&nbsp;

<span style="font-weight: 400;">This is a <em>fine-grained authorization mechanism</em> because:</span>

&nbsp;

  1.  <span style="font-weight: 400;">    Each API endpoint can be <strong>assigned a different set of scope(s)</strong></span>
  2.  <span style="font-weight: 400;">  </span> <span style="font-weight: 400;"> Each type of operation on a given API endpoint can be <strong>assigned a different set of scope(s)</strong></span>

&nbsp;

<span style="font-weight: 400;">Audit capabilities in Express Gateway are based upon customizable logging options. The administrator can include a customizable log message for each pipeline, that will apply to each incoming request on that pipeline. By including important request parameters like IP address, user id,  request URL, etc., each request can be analyzed for malicious activities.</span>

&nbsp;

<table style="border-style: dotted; height: 42px; width: 633px;">
  <tr style="height: 21px;">
    <td style="width: 289.375px; height: 21px;">
      <b>Authentication</b>
    </td>
    
    <td style="width: 168.264px; height: 21px;">
      <b> Authorization</b>
    </td>
    
    <td style="width: 158.264px; height: 21px;">
      <b>Audit</b>
    </td>
  </tr>
  
  <tr style="height: 21px;">
    <td style="width: 289.375px; height: 21px;">
      <b>basic-auth</b><span style="font-weight: 400;"> / </span><b>key-auth</b><span style="font-weight: 400;"> / </span><b>oauth </b><span style="font-weight: 400;">policy</span>
    </td>
    
    <td style="width: 168.264px; height: 21px;">
      <b>scopes</b>
    </td>
    
    <td style="width: 158.264px; height: 21px;">
      <b>log</b><span style="font-weight: 400;"> policy</span>
    </td>
  </tr>
</table>

&nbsp;

<span style="font-weight: 400;">Express Gateway allows us to create API endpoints and then control how client requests for any given endpoint is handled. This is achieved by defining a pipeline for each endpoint and placing a set of &#8216;policies&#8217; in a specific order in the pipeline. Express Gateway is built on top of the Node.js Express framework, and the policies are akin to Express.js middleware. Authentication is set up by adding one of the three policies: &#8216;basic-auth&#8217;, &#8216;key-auth&#8217; or &#8216;oauth&#8217; to a pipeline. Audit logs can be enabled by adding the &#8216;log&#8217; policy. Authorization (scopes) is an attribute of an API endpoint and is not implemented as a policy.</span>

&nbsp;

## **An Enterprise Use Case for Express Serverless Platform**

<span style="font-weight: 400;">First, we will work with a simple API endpoint that simply supplies the</span> [<span style="font-weight: 400;">Coordinated Universal Time</span>][2] <span style="font-weight: 400;">(UTC) now.</span>

&nbsp;

<span style="font-weight: 400;">To implement this API endpoint, we will make use of the existing URL:</span> [<span style="font-weight: 400;">http://worldclockapi.com/api/json/utc/now</span>][3] <span style="font-weight: 400;">, instead of reinventing the wheel. When we access this URL, we receive a response body containing the UTC time in JSON format:</span>

&nbsp;

<pre><span style="font-weight: 400;">{"$id":"1","currentDateTime":"2018-09-25T10:25Z","utcOffset":"00:00:00","isDayLightSavingsTime":false,"dayOfTheWeek":"Tuesday","timeZoneName":"UTC","currentFileTime":131823447213150424,"ordinalDate":"2018-268","serviceResponse":null}</span></pre>

&nbsp;

<span style="font-weight: 400;">Therefore, our job would be to create an API endpoint on the Express Serverless Platform, that wraps around the above URL. This API endpoint will respond with the current Universal Time. Furthermore, we will enforce authentication, authorization and audit on this API endpoint by applying suitable configuration settings.</span>

&nbsp;

<span style="font-weight: 400;">In a more realistic scenario, an organization using Express Serverless Platform would build a service on its own that it wants to expose externally as an API. But our goal is to focus on the traffic management feature. So we will try not to code a new service from scratch. Stay tuned, because in our next post we&#8217;ll dive head-first into technical detail on how to get this done.</span>

&nbsp;

If you&#8217;re interested in more of these topics, join the live discussion on twitter **([@lunchbadger][4])** or (**[@express_gateway).][5]**

* * *

  * [**Try out Express Serverless Platform**** **][6] &#8211; your feedback helps prioritize our roadmap with the most value realized within the shortest amount of time


<div class="spaced" style="padding-top:15px; clear:both;" >
</div>



 [1]: http://www.express-gateway.io?utm_source=content_mkt_apimgnt&utm_medium=blog&utm_campaign=2018-08-trial-launch&utm_content=link
 [2]: https://en.wikipedia.org/wiki/Coordinated_Universal_Time
 [3]: http://worldclockapi.com/api/json/utc/now
 [4]: http://www.twitter.com/lunchbadger
 [5]: https://twitter.com/express_gateway
 [6]: /getting-started/
 [7]: https://www.lunchbadger.com/express-api-gateway-enterprise-support?utm_source=content_mkt_apimgnt&utm_medium=blog&utm_campaign=2018-08-trial-launch&utm_content=link
 [8]: https://www.lunchbadger.com/express-gateway-enterprise/?utm_source=content_mkt_apimgnt&utm_medium=blog&utm_campaign=2018-08-trial-launch&utm_content=link
 [9]: http://eepurl.com/cSR5vT?utm_source=content_mkt_apimgnt&utm_medium=blog&utm_campaign=2018-08-trial-launch&utm_content=link