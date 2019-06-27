---
title: How To Get Started with API Management and Express Serverless Platform
menuTitle: "Get Started"
description: API Management begins with setting up the ServiceEndpoint. Get a step-by-step walkthrough of how to do this with Express Gateway, an API Gateway.
author: Monojit Basu
type: post
weight: 2
date: 2018-11-05T12:21:22+00:00
url: /blog/get-started-api-management-express-serverless-platform/
image: /uploads/2018/10/5.png
um_content_restriction:
  - 'a:8:{s:26:"_um_custom_access_settings";s:1:"0";s:14:"_um_accessible";s:1:"0";s:19:"_um_noaccess_action";s:1:"0";s:30:"_um_restrict_by_custom_message";s:1:"0";s:27:"_um_restrict_custom_message";s:0:"";s:19:"_um_access_redirect";s:1:"0";s:23:"_um_access_redirect_url";s:0:"";s:28:"_um_access_hide_from_queries";s:1:"0";}'
categories:
  - Development
  - Featured
tags:
  - API Consumer Management
  - api gateway
  - model-based microservices and serverless functions
  - Service Endpoint
  - Service Endpoint can be front-ended by an API Gateway

---
In our last post, we discussed API Management and the key role that an API Gateway could play. <span style="font-weight: 400;">API Gateways can enable secure access to its API endpoints. Features in an API Gateway are often categorized in three broad categories:</span>

  *  <span style="font-weight: 400;">        <strong>Authentication:</strong> Who is allowed to access (Access Control)</span>
  *  <span style="font-weight: 400;">        <strong>Authorization:</strong> Who is allowed to perform operations of exposed APIs (Permissions / Privileges)</span>
  *  <span style="font-weight: 400;">        <strong>Audit:</strong> Analyzing sufficient information for each client request </span>

<span style="font-weight: 400;">How does this work? How can developers and DevOps teams get started? We&#8217;ve broken out a step-by-step guide on how to get started with API Management with Express Serverless Platform including best practices on API Management along the way.</span>

Here&#8217;s a quick diagram of what that looks like:<figure class="post-image">

<img class="aligncenter size-full wp-image-5640" src="/wp-content/uploads/2018/10/Authorization-Graphics.png" alt="API Management in the Enterprise" width="600" height="300" srcset="/wp-content/uploads/2018/10/Authorization-Graphics.png 600w, /wp-content/uploads/2018/10/Authorization-Graphics-300x150.png 300w, /wp-content/uploads/2018/10/Authorization-Graphics-225x113.png 225w, /wp-content/uploads/2018/10/Authorization-Graphics-512x256.png 512w" sizes="(max-width: 600px) 100vw, 600px" /></figure> 

## **Setting Up The Service And API Endpoint in Express Serverless Platform**

<span style="font-weight: 400;">We will have to complete a few pre-requisite steps before configuring authentication, authorization and audit.</span>

  1. <span style="font-weight: 400;">First we have to set up a Service Endpoint using the Canvas</span>
  2.  <span style="font-weight: 400;"> </span><span style="font-weight: 400;">Then we have to set up a Gateway instance</span>

Before setting up a pipeline within this Gateway, it will be helpful to create a &#8216;scope&#8217; (which may be later associated with API endpoints and API users)

  1. <span style="font-weight: 400;">Then, we will create two users with credentials to access the APIs. For the purpose of this blog, we will work with Key-based Authentication.</span>
  2. <span style="font-weight: 400;">Finally we will set up a pipeline in our Gateway instance that is configured for authentication, authorization and audit</span>

<span style="font-weight: 400;">We have an existing service (worldclockapi.com) that we want to expose an API with appropriate rate limits. So, we need to drop in a &#8216;Service Endpoint&#8217; from the Canvas (on to the &#8216;Private&#8217; quadrant). This component only needs one configuration information: the </span>_<span style="font-weight: 400;">base</span>_ <span style="font-weight: 400;">URL of the service (</span>[<span style="font-weight: 400;">http://worldclockapi.com/api/json/utc/</span>][2]<span style="font-weight: 400;">).</span><figure class="post-image">

<img class="aligncenter size-full wp-image-5644" src="/wp-content/uploads/2018/10/API_Management_Service.jpg" alt="API Mangement - Setting up the Services" width="185" height="220" /></figure> 

<span style="font-weight: 400;"><img class="aligncenter size-full wp-image-5646" src="/wp-content/uploads/2018/10/pasted-image-0-copy.png" alt="API Mangement - Setting up the Services" width="628" height="251" srcset="/wp-content/uploads/2018/10/pasted-image-0-copy.png 628w, /wp-content/uploads/2018/10/pasted-image-0-copy-300x120.png 300w, /wp-content/uploads/2018/10/pasted-image-0-copy-225x90.png 225w, /wp-content/uploads/2018/10/pasted-image-0-copy-512x205.png 512w" sizes="(max-width: 628px) 100vw, 628px" /></span>

<span style="font-weight: 400;">The Service Endpoint can be front-ended by an API Gateway, just like other services (model-based microservices and serverless functions) in the Express Serverless Platform. So, next, we drop in a Gateway instance on the Gateway quadrant.</span><figure class="post-image">

<img class="aligncenter size-full wp-image-5647" src="/wp-content/uploads/2018/10/pasted-image-0-4.png" alt="API Management - Setting up the Services" width="629" height="245" srcset="/wp-content/uploads/2018/10/pasted-image-0-4.png 629w, /wp-content/uploads/2018/10/pasted-image-0-4-300x117.png 300w, /wp-content/uploads/2018/10/pasted-image-0-4-225x88.png 225w, /wp-content/uploads/2018/10/pasted-image-0-4-512x199.png 512w" sizes="(max-width: 629px) 100vw, 629px" /></figure> 

&nbsp;

<span style="font-weight: 400;">Before we jump into creating a pipeline, we will create a scope, and two users by clicking on the &#8216;Consumer Management&#8217; button on the Gateway element on our Canvas.</span>

<span style="font-weight: 400;">To create a new scope, we will navigate to the &#8216;Scopes&#8217; tab under Consumer Management.</span><figure class="post-image">

<img class="aligncenter size-full wp-image-5648" src="/wp-content/uploads/2018/10/pasted-image-0-4-1.png" alt="API Management - Setting up the Services" width="630" height="317" srcset="/wp-content/uploads/2018/10/pasted-image-0-4-1.png 630w, /wp-content/uploads/2018/10/pasted-image-0-4-1-300x151.png 300w, /wp-content/uploads/2018/10/pasted-image-0-4-1-225x113.png 225w, /wp-content/uploads/2018/10/pasted-image-0-4-1-509x256.png 509w" sizes="(max-width: 630px) 100vw, 630px" /></figure> 

&nbsp;

<span style="font-weight: 400;">Now we will create a scope named &#8216;timewatchers&#8217;. we just need to type in the scope name and hit &#8216;Enter&#8217;.</span>

&nbsp;<figure class="post-image">

<img class="aligncenter size-full wp-image-5649" src="/wp-content/uploads/2018/10/pasted-image-0-4-2.png" alt="API Management - Setting up the Services" width="631" height="315" srcset="/wp-content/uploads/2018/10/pasted-image-0-4-2.png 631w, /wp-content/uploads/2018/10/pasted-image-0-4-2-300x150.png 300w, /wp-content/uploads/2018/10/pasted-image-0-4-2-225x112.png 225w, /wp-content/uploads/2018/10/pasted-image-0-4-2-512x256.png 512w" sizes="(max-width: 631px) 100vw, 631px" /></figure> 

&nbsp;

<span style="font-weight: 400;">Now we will create a new user with user id &#8216;bob&#8217; and set up the following:</span>

  1.  <span style="font-weight: 400;">    Allocate a API key for key-based authentication for this user</span>
  2.  <span style="font-weight: 400;">  </span> <span style="font-weight: 400;"> Associate this user with the &#8216;timewatchers&#8217; scope</span>

<span style="font-weight: 400;">First we create a user &#8216;bob&#8217; from the &#8216;User&#8217; tab under Consumer Management.</span>

&nbsp;<figure class="post-image">

<img class="aligncenter size-full wp-image-5650" src="/wp-content/uploads/2018/10/pasted-image-0-4-3.png" alt="API Management - Setting up the Services" width="628" height="317" srcset="/wp-content/uploads/2018/10/pasted-image-0-4-3.png 628w, /wp-content/uploads/2018/10/pasted-image-0-4-3-300x151.png 300w, /wp-content/uploads/2018/10/pasted-image-0-4-3-225x114.png 225w, /wp-content/uploads/2018/10/pasted-image-0-4-3-507x256.png 507w" sizes="(max-width: 628px) 100vw, 628px" /></figure> 

&nbsp;

<span style="font-weight: 400;">To allocate an API key, expand the information on user bob from the &#8216;User&#8217; tab under Consumer Management.</span>

&nbsp;

<span style="font-weight: 400;"><img class="aligncenter size-full wp-image-5651" src="/wp-content/uploads/2018/10/pasted-image-0-4-4.png" alt="API Management - Setting up the Services" width="631" height="323" srcset="/wp-content/uploads/2018/10/pasted-image-0-4-4.png 631w, /wp-content/uploads/2018/10/pasted-image-0-4-4-300x154.png 300w, /wp-content/uploads/2018/10/pasted-image-0-4-4-225x115.png 225w, /wp-content/uploads/2018/10/pasted-image-0-4-4-500x256.png 500w" sizes="(max-width: 631px) 100vw, 631px" /></span><figure class="post-image">

<img class="aligncenter size-full wp-image-5652" src="/wp-content/uploads/2018/10/pasted-image-0-4-5.png" alt="API Management - Setting up the Services" width="629" height="318" srcset="/wp-content/uploads/2018/10/pasted-image-0-4-5.png 629w, /wp-content/uploads/2018/10/pasted-image-0-4-5-300x152.png 300w, /wp-content/uploads/2018/10/pasted-image-0-4-5-225x114.png 225w, /wp-content/uploads/2018/10/pasted-image-0-4-5-506x256.png 506w" sizes="(max-width: 629px) 100vw, 629px" /></figure> 

<span style="font-weight: 400;">Scroll down the pop-up showin the user details for &#8216;bob&#8217;, and focus on the Key-based authentication section. Click on the &#8216;Create&#8217; button.</span>

&nbsp;<figure class="post-image">

<img class="aligncenter size-full wp-image-5653" src="/wp-content/uploads/2018/10/pasted-image-0-4-6.png" alt="API Management - Setting up the Services" width="626" height="314" srcset="/wp-content/uploads/2018/10/pasted-image-0-4-6.png 626w, /wp-content/uploads/2018/10/pasted-image-0-4-6-300x150.png 300w, /wp-content/uploads/2018/10/pasted-image-0-4-6-225x113.png 225w, /wp-content/uploads/2018/10/pasted-image-0-4-6-510x256.png 510w" sizes="(max-width: 626px) 100vw, 626px" /></figure> 

&nbsp;

<span style="font-weight: 400;">This will generate a Key id and secret for the user &#8216;bob&#8217;. We need to take note of these credentials in order to access API endpoints.</span><figure class="post-image">

<img class="aligncenter size-full wp-image-5654" src="/wp-content/uploads/2018/10/pasted-image-0-4-copy.png" alt="API Management - Setting up the Services" width="629" height="317" srcset="/wp-content/uploads/2018/10/pasted-image-0-4-copy.png 629w, /wp-content/uploads/2018/10/pasted-image-0-4-copy-300x151.png 300w, /wp-content/uploads/2018/10/pasted-image-0-4-copy-225x113.png 225w, /wp-content/uploads/2018/10/pasted-image-0-4-copy-508x256.png 508w" sizes="(max-width: 629px) 100vw, 629px" /></figure> 

&nbsp;

<span style="font-weight: 400;">Finally, we will associate the &#8216;timewatchers&#8217; scope with the user &#8216;bob&#8217;.</span>

&nbsp;<figure class="post-image">

<img class="aligncenter size-full wp-image-5655" src="/wp-content/uploads/2018/10/pasted-image-0-4-copy-2.png" alt="API Management - Setting up the Services" width="626" height="321" srcset="/wp-content/uploads/2018/10/pasted-image-0-4-copy-2.png 626w, /wp-content/uploads/2018/10/pasted-image-0-4-copy-2-300x154.png 300w, /wp-content/uploads/2018/10/pasted-image-0-4-copy-2-225x115.png 225w, /wp-content/uploads/2018/10/pasted-image-0-4-copy-2-499x256.png 499w" sizes="(max-width: 626px) 100vw, 626px" /></figure> 

&nbsp;

<span style="font-weight: 400;">We will actually create one more user &#8216;alice&#8217; and allocate API keys in a similar fashion. However, we will not assign any scope to this user.</span>

&nbsp;<figure class="post-image">

<img class="aligncenter size-full wp-image-5656" src="/wp-content/uploads/2018/10/pasted-image-0-4-copy-3.png" alt="API Management - Setting up the Services" width="625" height="316" srcset="/wp-content/uploads/2018/10/pasted-image-0-4-copy-3.png 625w, /wp-content/uploads/2018/10/pasted-image-0-4-copy-3-300x152.png 300w, /wp-content/uploads/2018/10/pasted-image-0-4-copy-3-225x114.png 225w, /wp-content/uploads/2018/10/pasted-image-0-4-copy-3-506x256.png 506w" sizes="(max-width: 625px) 100vw, 625px" /></figure> 

&nbsp;

<span style="font-weight: 400;">Now we are ready to set up a pipeline in our Gateway instance with key-based authentication enabled.</span>

&nbsp;<figure class="post-image">

<img class="aligncenter size-full wp-image-5657" src="/wp-content/uploads/2018/10/pasted-image-0-4-copy-4.png" alt="API Management - Setting up the Services" width="628" height="252" srcset="/wp-content/uploads/2018/10/pasted-image-0-4-copy-4.png 628w, /wp-content/uploads/2018/10/pasted-image-0-4-copy-4-300x120.png 300w, /wp-content/uploads/2018/10/pasted-image-0-4-copy-4-225x90.png 225w, /wp-content/uploads/2018/10/pasted-image-0-4-copy-4-512x205.png 512w" sizes="(max-width: 628px) 100vw, 628px" /></figure> 

&nbsp;

Now that we&#8217;ve covered how to set up the ServiceEndpoint, we&#8217;ll move on to Authentication. Authentication is an important key aspect to API Management. <span style="font-weight: 400;">To enable key-based authentication, we&#8217;ll add policies to our pipeline and provide a complete easy-to-follow guide written by developers for developers on how to set this up.</span>

&nbsp;

If you&#8217;re interested in more of these topics, join the live discussion on twitter **[@lunchbadger][3]** or **[@express_gateway][4]**

&nbsp;
&nbsp;

{{% button href="https://facebook.com/sharer/sharer.php?u=https%3A%2F%2Fexpress-serverless.io%2Fblog%2Fget-started-api-management-express-serverless-platform%2F" icon="fab fa-facebook" %}}Share{{% /button %}}

{{% button href="https://twitter.com/intent/tweet/?text=How%20To%20Get%20Started%20with%20API%20Management%20and%20Express%20Serverless%20Platform&amp;url=https%3A%2F%2Fexpress-serverless.io%2Fblog%2Fget-started-api-management-express-serverless-platform%2F" icon="fab fa-twitter" %}}Tweet{{% /button %}}

{{% button href="https://www.linkedin.com/shareArticle?mini=true&amp;url=https%3A%2F%2Fexpress-serverless.io%2Fblog%2Fget-started-api-management-express-serverless-platform%2F&amp;title=How%20To%20Get%20Started%20with%20API%20Management%20and%20Express%20Serverless%20Platform&amp;summary=How%20To%20Get%20Started%20with%20API%20Management%20and%20Express%20Serverless%20Platform&amp;source=https%3A%2F%2Fexpress-serverless.io%2Fblog%2Fget-started-api-management-express-serverless-platform%2F" icon="fab fa-linkedin" %}}Link{{% /button %}}



 
 [2]: http://worldclockapi.com/api/json/utc/
 [3]: http://www.twitter.com/lunchbadger
 [4]: https://twitter.com/express_gateway
