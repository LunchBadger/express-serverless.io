---
title: ESP vs Azure Functions
author: Valeri Karpov
description: Compare getting started on Azure Functions versus Express Serverless Platform on Azure using this easy to follow guide with the "Hello, World" experience.
weight: 3
type: post
date: 2018-03-22T22:38:26+00:00
url: /resources/get-started-azure-functions-vs-express-serverless-platform-tutorial/
image: /uploads/2018/03/Hello-World-in-LunchBadger-vs-Azure-Functions-.png
um_content_restriction:
  - 'a:8:{s:26:"_um_custom_access_settings";s:1:"0";s:14:"_um_accessible";s:1:"0";s:19:"_um_noaccess_action";s:1:"0";s:30:"_um_restrict_by_custom_message";s:1:"0";s:27:"_um_restrict_custom_message";s:0:"";s:19:"_um_access_redirect";s:1:"0";s:23:"_um_access_redirect_url";s:0:"";s:28:"_um_access_hide_from_queries";s:1:"0";}'
categories:
  - Technology
tags:
  - AWS Lambda
  - AWS Lambda versus Azure
  - Azure Function App
  - Azure UI
  - Create a resource in Azure Portal
  - Express Gateway
  - Getting started with Microsoft Azure
  - Hello world with Azure
  - HTTP Interafce
  - Microsofot Azure UI
  - Microsoft Azure
  - open source API

---
If you&#8217;re looking at getting started with Azure, we&#8217;ve put together a comprehensive &#8220;Hello, World&#8217; guide. In addition to Azure, we&#8217;ve put together a no-frills comparison of the getting started experience from the developer perspective. Learn more, build more and check out the latest from Val Karpov in this latest installment of our Developer Spotlight Series.

<a href="https://azure.microsoft.com/en-us/services/functions/" rel="nofollow">Azure Functions</a> are <a href="https://azure.microsoft.com/en-us/" rel="nofollow">Microsoft Azure&#8217;s</a> equivalent to <a href="https://aws.amazon.com/lambda/" rel="nofollow">AWS Lambda</a>. Like Lambda, Azure Functions let you write custom functions and expose them via an HTTP interface using <a href="https://azure.microsoft.com/en-us/services/api-management/" rel="nofollow">Azure API Management</a>. Express Serverless Platform offers a similar stack that lets you write Node.js APIs and expose those APIs through [Express Gateway][2]without vendor lock in. In this article, I&#8217;ll walk through setting up a rudimentary function and gateway in both Express Serverless Platform and Azure and discuss the tradeoffs of using one or the other.

## Azure Functions

Log in to the <a href="https://portal.azure.com/" rel="nofollow">Azure Portal</a> and click &#8220;Create a resource.&#8221; In Microsoft Azure, <a href="https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-overview#terminology" rel="nofollow">&#8220;resource&#8221;</a> is a very broad term that applies to any manageable service Azure offers you. A function, a VM, an IP address, and storage space are all distinct resources.

&nbsp;<figure class="post-image">

<img class="aligncenter size-full wp-image-3658" src="/wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f723349644277512e706e67.png" alt="Compare Azure and Express Serverless Platform"></figure> 

&nbsp;

Clicking on &#8220;Create a resource&#8221; will open up a new &#8220;blade&#8221; in the Azure UI. Blade is just a fancy name for a panel in the Azure UI. Click &#8220;Compute&#8221; and then &#8220;Function App&#8221; to create a new Function App. A Function App is a collection of individual functions.

&nbsp;<figure class="post-image">

<img class="aligncenter size-full wp-image-3659" src="/wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f3741324e616e382e706e67.png" alt="Compare Microsoft Azure and Express Serverless Platform" </figure>.

&nbsp;

Once you click &#8220;Function App&#8221;, you&#8217;ll see a blade that asks you for information about your Function App. Enter in a name, but be aware that your name needs to be unique across _all_ Azure function apps, so you should prefix the name with your name. For this example, there&#8217;s no need to change any of the other options. Notice that, by default, Azure Functions run on Windows. Ideally your functions shouldn&#8217;t care about what OS they run, so long as they&#8217;re running on the right version of Node.js, but this is something to be aware of if you are using Node.js C++ add-ons compiled with [node-gyp][3].

&nbsp;<figure class="post-image">

<img class="aligncenter size-full wp-image-3660" src="/wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f514643627161552e706e67.png" alt="Compare Microsoft Azure with LunchBadger" width="538" height="992" srcset="/wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f514643627161552e706e67.png 538w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f514643627161552e706e67-163x300.png 163w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f514643627161552e706e67-122x225.png 122w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f514643627161552e706e67-139x256.png 139w" sizes="(max-width: 538px) 100vw, 538px" /></figure> 

&nbsp;

Click &#8220;Create&#8221; and Azure will kick off creating your Function App. Click the bell icon on the upper right to look out for a notification that Azure finished creating your app.<figure class="post-image">

<img class="aligncenter size-full wp-image-3661" src="/wp-content/uploads/2018/03/37663494-b5bf46d6-2c2f-11e8-8208-fc0e5610bccf.png" alt="Compare Microsoft Azure with LunchBadger" width="843" height="343" srcset="/wp-content/uploads/2018/03/37663494-b5bf46d6-2c2f-11e8-8208-fc0e5610bccf.png 843w, /wp-content/uploads/2018/03/37663494-b5bf46d6-2c2f-11e8-8208-fc0e5610bccf-300x122.png 300w, /wp-content/uploads/2018/03/37663494-b5bf46d6-2c2f-11e8-8208-fc0e5610bccf-768x312.png 768w, /wp-content/uploads/2018/03/37663494-b5bf46d6-2c2f-11e8-8208-fc0e5610bccf-225x92.png 225w, /wp-content/uploads/2018/03/37663494-b5bf46d6-2c2f-11e8-8208-fc0e5610bccf-512x208.png 512w" sizes="(max-width: 843px) 100vw, 843px" /></figure> 

&nbsp;

Once Azure has created your app, click &#8220;Go to resource&#8221; to configure your Function App.

&nbsp;<figure class="post-image">

<img class="aligncenter size-full wp-image-3662" src="/wp-content/uploads/2018/03/37663610-f6f6b198-2c2f-11e8-804c-23ba7b046cca.png" alt="" width="424" height="379" srcset="/wp-content/uploads/2018/03/37663610-f6f6b198-2c2f-11e8-804c-23ba7b046cca.png 424w, /wp-content/uploads/2018/03/37663610-f6f6b198-2c2f-11e8-804c-23ba7b046cca-300x268.png 300w, /wp-content/uploads/2018/03/37663610-f6f6b198-2c2f-11e8-804c-23ba7b046cca-225x201.png 225w, /wp-content/uploads/2018/03/37663610-f6f6b198-2c2f-11e8-804c-23ba7b046cca-286x256.png 286w" sizes="(max-width: 424px) 100vw, 424px" /></figure> 

&nbsp;

**Remember** that a Function App is a collection of functions. Click the plus icon next to &#8220;Functions&#8221; to create a new function.

&nbsp;<figure class="post-image">

<img class="aligncenter size-full wp-image-3663" src="/wp-content/uploads/2018/03/37663687-20cb14be-2c30-11e8-89f9-122d98246d6a.png" alt="Compare Microsoft Azure with LunchBadger" width="430" height="327" srcset="/wp-content/uploads/2018/03/37663687-20cb14be-2c30-11e8-89f9-122d98246d6a.png 430w, /wp-content/uploads/2018/03/37663687-20cb14be-2c30-11e8-89f9-122d98246d6a-300x228.png 300w, /wp-content/uploads/2018/03/37663687-20cb14be-2c30-11e8-89f9-122d98246d6a-225x171.png 225w, /wp-content/uploads/2018/03/37663687-20cb14be-2c30-11e8-89f9-122d98246d6a-337x256.png 337w" sizes="(max-width: 430px) 100vw, 430px" /></figure> 

&nbsp;

Azure makes it easy to create a function that&#8217;s exposed via HTTP. Choose the &#8220;Webhook + API&#8221; scenario and &#8220;JavaScript&#8221; as your language, and then click &#8220;Create this function.&#8221;

&nbsp;<figure class="post-image">

<img class="aligncenter size-full wp-image-3664" src="/wp-content/uploads/2018/03/37663755-4af748de-2c30-11e8-98f6-ee749f95174f.png" alt="Compare Microsoft Azure with LunchBadger" width="1371" height="765" srcset="/wp-content/uploads/2018/03/37663755-4af748de-2c30-11e8-98f6-ee749f95174f.png 1371w, /wp-content/uploads/2018/03/37663755-4af748de-2c30-11e8-98f6-ee749f95174f-300x167.png 300w, /wp-content/uploads/2018/03/37663755-4af748de-2c30-11e8-98f6-ee749f95174f-768x429.png 768w, /wp-content/uploads/2018/03/37663755-4af748de-2c30-11e8-98f6-ee749f95174f-1024x571.png 1024w, /wp-content/uploads/2018/03/37663755-4af748de-2c30-11e8-98f6-ee749f95174f-225x126.png 225w, /wp-content/uploads/2018/03/37663755-4af748de-2c30-11e8-98f6-ee749f95174f-459x256.png 459w" sizes="(max-width: 1371px) 100vw, 1371px" /></figure> 

&nbsp;

Azure will create a new &#8220;Hello, world&#8221; function for you. Change the code to print out the current Node.js version as well, and click &#8220;Save and run&#8221; to execute this function

<pre>module.exports = function (context, req) {
 context.log('JavaScript HTTP trigger function processed a request.');
 if (req.body.name) {
    context.res = {
    // status: 200, /* Defaults to 200 */
    body: 'Hello ' + req.body.name + ' from Node.js ' + process.version
    };
    }
    else {
    context.res = {
    status: 400,
    body: "Please pass a name on the query string or in the request body"
    };
    }
    context.done();
    };

</pre><figure class="post-image">

<img class="aligncenter size-full wp-image-3665" src="/wp-content/uploads/2018/03/37664177-2a2f4e5c-2c31-11e8-844c-2fdabed20cfb.png" alt="Compare Microsoft Azure with LunchBadger" width="1696" height="912" srcset="/wp-content/uploads/2018/03/37664177-2a2f4e5c-2c31-11e8-844c-2fdabed20cfb.png 1696w, /wp-content/uploads/2018/03/37664177-2a2f4e5c-2c31-11e8-844c-2fdabed20cfb-300x161.png 300w, /wp-content/uploads/2018/03/37664177-2a2f4e5c-2c31-11e8-844c-2fdabed20cfb-768x413.png 768w, /wp-content/uploads/2018/03/37664177-2a2f4e5c-2c31-11e8-844c-2fdabed20cfb-1024x551.png 1024w, /wp-content/uploads/2018/03/37664177-2a2f4e5c-2c31-11e8-844c-2fdabed20cfb-225x121.png 225w, /wp-content/uploads/2018/03/37664177-2a2f4e5c-2c31-11e8-844c-2fdabed20cfb-476x256.png 476w" sizes="(max-width: 1696px) 100vw, 1696px" /></figure> 

&nbsp;

Click on &#8220;Get function URL&#8221; to get the publicly accessible URL for your function. Azure will automatically generate a key for you so your endpoint has some rudimentary security.

&nbsp;<figure class="post-image">

<img class="aligncenter size-full wp-image-3666" src="/wp-content/uploads/2018/03/37664268-56324982-2c31-11e8-98a0-03410f68130f.png" alt="Compare Microsoft Azure with LunchBadger" width="956" height="441" srcset="/wp-content/uploads/2018/03/37664268-56324982-2c31-11e8-98a0-03410f68130f.png 956w, /wp-content/uploads/2018/03/37664268-56324982-2c31-11e8-98a0-03410f68130f-300x138.png 300w, /wp-content/uploads/2018/03/37664268-56324982-2c31-11e8-98a0-03410f68130f-768x354.png 768w, /wp-content/uploads/2018/03/37664268-56324982-2c31-11e8-98a0-03410f68130f-225x104.png 225w, /wp-content/uploads/2018/03/37664268-56324982-2c31-11e8-98a0-03410f68130f-512x236.png 512w" sizes="(max-width: 956px) 100vw, 956px" /></figure> 

&nbsp;

You should now be able to access your function using <a href="https://en.wikipedia.org/wiki/CURL" rel="nofollow">curl</a>.

<pre>$ curl -H "Content-Type: application/json" -X POST -d '{"name":"curl"}' https://vkarpov15-test.azurewebsites.net/api/HttpTriggerJS1?code=OMITTED
 "Hello curl from Node.js v6.11.2"
 $</pre>

Note that, by default, Azure currently uses Node.js v6.11.2. You can <a href="https://docs.microsoft.com/en-us/azure/azure-functions/functions-reference-node#node-version-and-package-management" rel="nofollow">configure this using </p> 

<div class="codecolorer-container text default" style="overflow:auto;white-space:nowrap;width:435px;">
  <div class="text codecolorer">
    package.json
  </div>
</div>

<p>
  </a>, so you should be able to use Node.js 8 and <a href="http://thecodebarbarian.com/common-async-await-design-patterns-in-node.js.html" rel="nofollow">async/await</a> with Azure Functions.
</p>

<div class="spaced" style="padding-top:15px; clear:both;" >
</div>

<h2>
  <strong>Express Serverless Platform and Express Gateway</strong>
</h2>

<p>
  In Express Serverless Platform, first create a new function and name it &#8216;myfunction&#8217;:<br /> <img class="aligncenter size-full wp-image-3667" src="/wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f427062785041662e706e67.png" alt="LunchBadger and Express Gateway" width="1434" height="428" srcset="/wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f427062785041662e706e67.png 1434w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f427062785041662e706e67-300x90.png 300w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f427062785041662e706e67-768x229.png 768w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f427062785041662e706e67-1024x306.png 1024w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f427062785041662e706e67-225x67.png 225w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f427062785041662e706e67-512x153.png 512w" sizes="(max-width: 1434px) 100vw, 1434px" />
</p>

<p>
  Node.js functions in Express Serverless Platform have the same function signature as <a href="https://nodejs.org/api/http.html#http_event_request" rel="nofollow">native Node.js HTTP request listeners</a>. The function to print &#8216;Hello, world!&#8217; with Express Serverless Platformis shown below. Note that the exported function <strong>must</strong> have the same name as the function name you assigned in the LunchBadger GUI.
</p>

<pre>module.exports = {
 myfunction (req, res) {
 res.end('Hello, world!');
 }
 };

</pre><figure class="post-image">

<img class="aligncenter size-full wp-image-3668" src="/wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f50684967536f7a2e706e67.png" alt="Compare Microsoft Azure with LunchBadger" width="1716" height="975" srcset="/wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f50684967536f7a2e706e67.png 1716w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f50684967536f7a2e706e67-300x170.png 300w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f50684967536f7a2e706e67-768x436.png 768w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f50684967536f7a2e706e67-1024x582.png 1024w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f50684967536f7a2e706e67-225x128.png 225w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f50684967536f7a2e706e67-451x256.png 451w" sizes="(max-width: 1716px) 100vw, 1716px" /></figure> 

<p>
  &nbsp;
</p>

<p>
  Note that this function does not have to create an actual HTTP server.Express Serverless Platform handles creating a server for you, so you can write &#8220;serverless&#8221; functions without having to actually write an <a href="https://www.npmjs.com/package/express" rel="nofollow">express</a> application. You do still get access to the <a href="https://nodejs.org/api/http.html#http_class_http_serverresponse" rel="nofollow">Node.js HTTP response</a>, so you can set HTTP headers and set the <a href="https://en.wikipedia.org/wiki/List_of_HTTP_status_codes" rel="nofollow">HTTP status code</a>.
</p>

<p>
  From the menu on the left, add a new gateway. This will add an <a href="http://www.express-gateway.io?utm_source=Comparison_GS_Azure&utm_medium=blog&utm_campaign=2018-10-comparisons&utm_content=link">Express Gateway</a> instance to your project.
</p>

<p>
  &nbsp;
</p><figure class="post-image">

<img class="aligncenter size-full wp-image-3669" src="/wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f777249315848442e706e67.png" alt="Compare Microsoft Azure with LunchBadger" width="1339" height="621" srcset="/wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f777249315848442e706e67.png 1339w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f777249315848442e706e67-300x139.png 300w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f777249315848442e706e67-768x356.png 768w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f777249315848442e706e67-1024x475.png 1024w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f777249315848442e706e67-225x104.png 225w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f777249315848442e706e67-512x237.png 512w" sizes="(max-width: 1339px) 100vw, 1339px" /></figure> 

<p>
  &nbsp;
</p>

<p>
  Click the plus icon next to &#8220;Policies&#8221; to add a policy to the default<a href="https://www.express-gateway.io/docs/core-concepts#pipelines?utm_source=Comparison_GS_Azure&utm_medium=blog&utm_campaign=2018-10-comparisons&utm_content=link"> Express Gateway pipeline.</a> In Express Gateway, a pipeline is a sequence of <a href="https://www.express-gateway.io/docs/core-concepts#policies?utm_source=Comparison_GS_Azure&utm_medium=blog&utm_campaign=2018-10-comparisons&utm_content=link">policies </a>for handling a request. Add an empty &#8216;proxy&#8217; pipeline.
</p>

<p>
  &nbsp;
</p><figure class="post-image">

<img class="aligncenter size-full wp-image-3670" src="/wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f6a35374e5366512e706e67.png" alt="Compare Microsoft Azure with LunchBadger" width="1509" height="655" srcset="/wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f6a35374e5366512e706e67.png 1509w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f6a35374e5366512e706e67-300x130.png 300w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f6a35374e5366512e706e67-768x333.png 768w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f6a35374e5366512e706e67-1024x444.png 1024w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f6a35374e5366512e706e67-225x98.png 225w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f6a35374e5366512e706e67-512x222.png 512w" sizes="(max-width: 1509px) 100vw, 1509px" /></figure> 

<p>
  &nbsp;
</p>

<p>
  Drag a line from your gateway to your function, and Express Serverless Platform will automatically connect your proxy policy to your function.
</p>

<p>
  &nbsp;
</p><figure class="post-image">

<img class="aligncenter size-full wp-image-3671" src="/wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f44726c5a7a4b652e706e67.png" alt="Compare Microsoft Azure with LunchBadger" width="1918" height="673" srcset="/wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f44726c5a7a4b652e706e67.png 1918w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f44726c5a7a4b652e706e67-300x105.png 300w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f44726c5a7a4b652e706e67-768x269.png 768w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f44726c5a7a4b652e706e67-1024x359.png 1024w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f44726c5a7a4b652e706e67-225x79.png 225w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f44726c5a7a4b652e706e67-512x180.png 512w" sizes="(max-width: 1918px) 100vw, 1918px" /></figure> 

<p>
  &nbsp;
</p>

<p>
  Express Serverless Platform will also create a function endpoint for you. Keep the &#8220;paths&#8221; for your function endpoint empty for now. Click on the &#8220;settings&#8221; icon to find the publicly accessible URL for your Express Serverless Platform project.
</p>

<p>
  &nbsp;
</p><figure class="post-image">

<img class="aligncenter size-full wp-image-3672" src="/wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f344232736e61312e706e67.png" alt="Compare Microsoft Azure with LunchBadger" width="1918" height="871" srcset="/wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f344232736e61312e706e67.png 1918w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f344232736e61312e706e67-300x136.png 300w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f344232736e61312e706e67-768x349.png 768w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f344232736e61312e706e67-1024x465.png 1024w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f344232736e61312e706e67-225x102.png 225w, /wp-content/uploads/2018/03/68747470733a2f2f692e696d6775722e636f6d2f344232736e61312e706e67-512x233.png 512w" sizes="(max-width: 1918px) 100vw, 1918px" /></figure> 

<p>
  &nbsp;
</p>

<p>
  Running curl on the URL will now run your custom function and give you the &#8220;Hello, world!&#8221; text.
</p>

<pre>$ curl http://gateway-148-dev.lunchbadger.io
 Hello, World!
 $</pre>

<h2>
  Moving On
</h2>

<p>
  The combination of Express Serverless Platform and Express Gateway is a great alternative to Azure Functions if you&#8217;re looking to avoid vendor lock-in. In particular, the fact that Express Serverless Platform scaffolds out an app for you and stores it in a git repo that you can clone enables you to run your app locally or on any cloud provider. Express Serverless Platform does automatically host your app for you, but that isn&#8217;t your only option.
</p>

<p>
  With Azure Functions, you can&#8217;t clone your whole stack and run it locally. You can run your functions locally, but the API Management part of the stack lives exclusively in Microsoft Azure. Azure is appealing because Microsoft is a well-established company and Azure has a proven track record of running applications at massive scale.
</p>

<p>
  However, using Azure Functions means you must run your code on Azure and use Azure API Management, so you can&#8217;t run your full app locally or on another cloud provider.
</p>

<p>
  &nbsp;
</p>

<p>
  This short video demonstrates Express Serverless Platform running on Azure. The demo utilizes a SOAP connector to interface with a legacy customer SOAP service and creates a new facade called a credit application through a model function.
</p>

<p>
  &nbsp;
</p>

<p style="text-align: center;">
  <iframe src="https://player.vimeo.com/video/325338092" width="640" height="360" frameborder="0" allowfullscreen="allowfullscreen"></iframe>
</p>

<p>
  &nbsp;
</p>

<p>
  &nbsp;
</p>

<p>
  We&#8217;ve written a complete guide towards understanding the major differences and similarities between Express Serverless Platform on Azure versus Azure Functions across multiple dimensions, including features and pricing, which is available for download from our <a href="/resources/pdf-guides/" target="_blank">Resources page.</a>

</p>



<p>
  Additionally, if you&#8217;re interested in more of these topics, join the live discussion on twitter <strong><a href="http://www.twitter.com/lunchbadger">@lunchbadger</a></strong> or <strong><a href="https://twitter.com/express_gateway">@express_gateway.</a></strong>
</p>

<hr />
&nbsp;
&nbsp;

{{% button href="https://facebook.com/sharer/sharer.php?u=https%3A%2F%2Fexpress-serverless.io%2Fresources%2Fget-started-azure-functions-vs-express-serverless-platform-tutorial%2F" icon="fab fa-facebook" %}}Share{{% /button %}}

{{% button href="https://twitter.com/intent/tweet/?text=ESP%20vs%20Azure%20Functions&amp;url=https%3A%2F%2Fexpress-serverless.io%2Fresources%2Fget-started-azure-functions-vs-express-serverless-platform-tutorial%2F" icon="fab fa-twitter" %}}Tweet{{% /button %}}

{{% button href="https://www.linkedin.com/shareArticle?mini=true&amp;url=https%3A%2F%2Fexpress-serverless.io%2Fresources%2Fget-started-azure-functions-vs-express-serverless-platform-tutorial%2F&amp;title=ESP%20vs%20Azure%20Functions&amp;summary=ESP%20vs%20Azure%20Functions&amp;source=https%3A%2F%2Fexpress-serverless.io%2Fresources%2Fget-started-azure-functions-vs-express-serverless-platform-tutorial%2F" icon="fab fa-linkedin" %}}Link{{% /button %}}




 [1]: https://www.lunchbadger.com/express-serverless-platform/?utm_source=Comparison_GS_Azure&utm_medium=blog&utm_campaign=2018-10-comparisons&utm_content=link
 [2]: http://www.express-gateway.io?utm_source=Comparison_GS_Azure&utm_medium=blog&utm_campaign=2018-10-comparisons&utm_content=link
 [3]: https://github.com/nodejs/node-gyp