---
title: API Management - Setting Up Key-Based Authentication
menuTitle: Key Based Authentication
author: Monojit Basu
weight: 3
type: post
date: 2018-11-08T09:09:25+00:00
url: /blog/api-management-setting-up-key-based-authentication-with-express-serverless-platform/
featured_image: /wp-content/uploads/2018/11/3-225x113.png
um_content_restriction:
  - 'a:8:{s:26:"_um_custom_access_settings";s:1:"0";s:14:"_um_accessible";s:1:"0";s:19:"_um_noaccess_action";s:1:"0";s:30:"_um_restrict_by_custom_message";s:1:"0";s:27:"_um_restrict_custom_message";s:0:"";s:19:"_um_access_redirect";s:1:"0";s:23:"_um_access_redirect_url";s:0:"";s:28:"_um_access_hide_from_queries";s:1:"0";}'
categories:
  - Development
  - Featured
tags:
  - API endpoints
  - API keys sent over HTTPS
  - best practices on API Management
  - end-to-end request path from the API endpoint to the back-end service
  - key-auth policy
  - Proxy policy

---
We&#8217;ve  discussed API Management and [setting up the Service and API Endpoints][2]. As long time champions of all the ways you could be using an API Gateway, we&#8217;re going to walk through how take the next step with API Management and set up your Authentication.

<span style="font-weight: 400;">To recap, features in an API Gateway are often categorized in three broad categories:</span>

  *  <span style="font-weight: 400;">        <strong>Authentication:</strong> Who is allowed to access (Access Control)</span>
  *  <span style="font-weight: 400;">        <strong>Authorization:</strong> Who is allowed to perform operations of exposed APIs (Permissions / Privileges)</span>
  *  <span style="font-weight: 400;">        <strong>Audit:</strong> Analyzing sufficient information for each client request </span>

Here&#8217;s a quick diagram of what that looks like:<figure class="post-image">

<img class="aligncenter size-full wp-image-5640" src="https://www.lunchbadger.com/wp-content/uploads/2018/10/Authorization-Graphics.png" alt="API Management in the Enterprise" width="600" height="300" srcset="https://www.lunchbadger.com/wp-content/uploads/2018/10/Authorization-Graphics.png 600w, https://www.lunchbadger.com/wp-content/uploads/2018/10/Authorization-Graphics-300x150.png 300w, https://www.lunchbadger.com/wp-content/uploads/2018/10/Authorization-Graphics-225x113.png 225w, https://www.lunchbadger.com/wp-content/uploads/2018/10/Authorization-Graphics-512x256.png 512w" sizes="(max-width: 600px) 100vw, 600px" /></figure> 

<span style="font-weight: 400;">How does all of this work together?  We&#8217;ve broken out a step-by-step guide on how to get started with setting up key-based authentication  with Express Serverless Platform including best practices on API Management along the way.</span>

## **How To Set Up Key-Based Authentication **

<span style="font-weight: 400;">To enable key-based authentication, we recommend adding two policies in our pipeline in this order: </span>

  * <span style="font-weight: 400;">key-auth, and</span>
  * proxy

Check it out:<figure class="post-image">

<img class="aligncenter size-full wp-image-5750" src="https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-5.png" alt="Setting Up Authentication" width="631" height="313" srcset="https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-5.png 631w, https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-5-300x149.png 300w, https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-5-225x112.png 225w, https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-5-512x254.png 512w" sizes="(max-width: 631px) 100vw, 631px" /></figure> 

&nbsp;<figure class="post-image">

<img class="aligncenter size-full wp-image-5751" src="https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-5-copy.png" alt="Setting Up Authentication" width="628" height="324" srcset="https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-5-copy.png 628w, https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-5-copy-300x155.png 300w, https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-5-copy-225x116.png 225w, https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-5-copy-496x256.png 496w" sizes="(max-width: 628px) 100vw, 628px" /></figure> 

&nbsp;

&nbsp;

<span style="font-weight: 400;">Now we will connect our Service Endpoint to the pipeline just created. The first time we do so, an API Endpoint will be automatically created in the &#8216;Public&#8217; quadrant and connected to the Gateway. This creates an end-to-end request path from the API Endpoint to the back-end service.</span>

&nbsp;<figure class="post-image">

<img class="aligncenter size-full wp-image-5752" src="https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-1.png" alt="Setting Up Authentication" width="627" height="316" srcset="https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-1.png 627w, https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-1-300x151.png 300w, https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-1-225x113.png 225w, https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-1-508x256.png 508w" sizes="(max-width: 627px) 100vw, 627px" /></figure> 

&nbsp;

<span style="font-weight: 400;">The API Endpoint will expect a path to be specified. Here we have specified the path &#8216;/now&#8217;. </span>

<span style="font-weight: 400;">So, when a request comes into the Express Serverless Platform for the URL: <API Endpoint Root URL>/now, it is routed to the URL: <Service Endpoint Base URL>/now. So effectively, the response will come from the backend service.</span>

**Testing**<span style="font-weight: 400;">: Now the API end-point should be accessible to an authenticated user.</span>

<span style="font-weight: 400;">First let us simply access it without supplying credentials for key-based authentication.</span>

&nbsp;<figure class="post-image">

<img class="aligncenter size-full wp-image-5753" src="https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-2.png" alt="Setting Up Authentication" width="628" height="67" srcset="https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-2.png 628w, https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-2-300x32.png 300w, https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-2-225x24.png 225w, https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-2-512x55.png 512w" sizes="(max-width: 628px) 100vw, 628px" /></figure> 

&nbsp;

<span style="font-weight: 400;">We get a message &#8216;Unauthorized&#8217;, which is expected.</span>

<span style="font-weight: 400;">Now we access the API as user &#8216;bob&#8217;. We will receive a response indicating current UTC time, from the back-end service. To send the key-based authentication credentials, the request should be as follows:</span>

<span style="font-weight: 400;">curl -H &#8220;Authorization: apiKey ${keyId}:${keySecret}&#8221; <API Endpoint></span>

&nbsp;<figure class="post-image">

<img class="aligncenter size-full wp-image-5754" src="https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-5-copy-2.png" alt="Setting Up Authentication" width="628" height="111" srcset="https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-5-copy-2.png 628w, https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-5-copy-2-300x53.png 300w, https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-5-copy-2-225x40.png 225w, https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-5-copy-2-512x90.png 512w" sizes="(max-width: 628px) 100vw, 628px" /></figure> 

<span style="font-weight: 400;">User &#8216;alice&#8217; would also be able to access the API as shown below.</span>

&nbsp;<figure class="post-image">

<img class="aligncenter size-full wp-image-5755" src="https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-2-copy.png" alt="Setting Up Authentication" width="628" height="108" srcset="https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-2-copy.png 628w, https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-2-copy-300x52.png 300w, https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-2-copy-225x39.png 225w, https://www.lunchbadger.com/wp-content/uploads/2018/11/pasted-image-0-2-copy-512x88.png 512w" sizes="(max-width: 628px) 100vw, 628px" /></figure> 

&nbsp;

<span style="font-weight: 400;"><strong>Pro Tip:</strong> <em>API keys should only be sent over HTTPS, so that it is not intercepted on the wire. Note that Express Serverless Platform by default creates API Endpoints that are secured using HTTPS protocol.</em></span>

&nbsp;

If you&#8217;re interested in more of these topics, join the live discussion on twitter **[@lunchbadger][3]** or **[@express_gateway.][4]**

&nbsp;
&nbsp;

{{% button href="https://facebook.com/sharer/sharer.php?u=https%3A%2F%2Fexpress-serverless.io%2Fblog%2Fapi-management-setting-up-key-based-authentication-with-express-serverless-platform%2F" icon="fab fa-facebook" %}}Share{{% /button %}}

{{% button href="https://twitter.com/intent/tweet/?text=API%20Management%20-%20Setting%20Up%20Key-Based%20Authentication&amp;url=https%3A%2F%2Fexpress-serverless.io%2Fblog%2Fapi-management-setting-up-key-based-authentication-with-express-serverless-platform%2F" icon="fab fa-twitter" %}}Tweet{{% /button %}}

{{% button href="https://www.linkedin.com/shareArticle?mini=true&amp;url=https%3A%2F%2Fexpress-serverless.io%2Fblog%2Fapi-management-setting-up-key-based-authentication-with-express-serverless-platform%2F&amp;title=API%20Management%20-%20Setting%20Up%20Key-Based%20Authentication&amp;summary=API%20Management%20-%20Setting%20Up%20Key-Based%20Authentication&amp;source=https%3A%2F%2Fexpress-serverless.io%2Fblog%2Fapi-management-setting-up-key-based-authentication-with-express-serverless-platform%2F" icon="fab fa-linkedin" %}}Link{{% /button %}}



 [1]: https://www.lunchbadger.com/api-management-authentication-authorization-audit/
 [2]: /blog/get-started-api-management-express-serverless-platform/
 [3]: http://www.twitter.com/lunchbadger
 [4]: https://twitter.com/express_gateway
 [5]: https://www.lunchbadger.com/express-serverless-platform/?utm_source=content_mkt_apimgnt3&utm_medium=blog&utm_campaign=2018-08-trial-launch&utm_content=link
 [6]: https://www.lunchbadger.com/express-api-gateway-enterprise-support?utm_source=content_mkt_apimgnt&utm_medium=blog&utm_campaign=2018-08-trial-launch&utm_content=link
 [7]: https://www.lunchbadger.com/express-gateway-enterprise/?utm_source=content_mkt_apimgnt3&utm_medium=blog&utm_campaign=2018-08-trial-launch&utm_content=link
 [8]: http://eepurl.com/cSR5vT?utm_source=content_mkt_apimgnt3&utm_medium=blog&utm_campaign=2018-08-trial-launch&utm_content=link