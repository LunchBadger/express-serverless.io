---
title: Hello World with Express Serverless Platform vs Apigee Edge
menuTitle: ESP vs Apigee Edge
weight: 5
author: Valeri Karpov
type: post
date: 2018-03-15T13:00:05+00:00
url: /blog/vs-apigee-features/
featured_image: /wp-content/uploads/2018/03/4Multi-Cloud-Kubernetes-and-Our-New-Partnership-with-Joyent-225x113.png
categories:
  - Technology
tags:
  - api gateway
  - API Proxies
  - Apigee Edge
  - express.js
  - Google
  - Google acquired Apigee
  - How do I deploy an API gateway?
  - How to Deploy an API Proxy?
  - Node
  - Node.js
  - What is Apigee Edge

---

[Apigee Edge][1] ([acquired by Google in 2016][2]) is a popular platform for deploying API proxies. Express Serverless Platform, like Apigee, allows you to build and deploy API gateways on their internal cloud computing service. At a high level, Express Serverless Platform and Apigee are similar, but there are several key differences in terms of Node.js version compatibility and vendor lock-in that you should be aware of before choosing one or the other.

## Deploying a Node.js Application to Apigee Edge

Before you deploy a Node.js app to Apigee, you need to be aware that <a href="https://community.apigee.com/questions/23770/upgrading-edges-version-of-node.html" rel="nofollow">Apigee currently only supports Node.js v0.10.32</a>. There is no way to use another version. [Node.js 0.10.32 was released in 2014][4] and  [formally deprecated since 2016][5]. Therefore, many modern Node.js libraries will not work on Apigee.

&nbsp;

To create a new API Gateway with Apigee, log into the Apigee Edge console and click on &#8220;API Proxies.&#8221;:

&nbsp;<figure class="post-image">

![][6]</figure> 

&nbsp;

Click on the add proxy button on the upper right corner to create a new proxy.

&nbsp;<figure class="post-image">

![][7]</figure> 

For a fair comparison with Express Serverless Platform, click &#8220;Node.js App&#8221; to create a new Node application, and upload the below hello-apigee.js file. Note that with Apigee, your Node.js app needs to expose an HTTP server, Apigee does **not** currently support any sort of function-as-a-service interface.

&nbsp;

<pre>var http = require('http');

var svr = http.createServer(function(req, resp) {
 resp.writeHead(200, { 'Content-Type': 'text/plain' });
 resp.end('Hello, World! ' + process.version + '\n');
 });

svr.listen(9000, function() {
 console.log('The server is listening on port 9000');
 });

</pre>

&nbsp;<figure class="post-image">

![][8]</figure> 

&nbsp;

In the &#8220;Security&#8221; step, select &#8220;Pass through&#8221; so make it easy to access your API Gateway. In production you would likely set API Key security here, but for this simple example you shouldn&#8217;t set up any security.

&nbsp;<figure class="post-image">

![][9]</figure> 

&nbsp;

For the &#8220;Virtual Hosts&#8221; and &#8220;Build&#8221; steps, just hit next and skip those steps. When you get to the &#8220;Summary&#8221; step, Apigee will deploy your API Gateway for you.

&nbsp;<figure class="post-image">

![][10]</figure> 

&nbsp;

Once your API Gateway is finished deploying, you should be able to access your endpoint using <a href="https://en.wikipedia.org/wiki/CURL" rel="nofollow">curl</a>. _Note: once again that the Node.js version is v0.10.32._

&nbsp;

<pre><div class="codecolorer-container text default" style="overflow:auto;white-space:nowrap;width:435px;">
  <div class="text codecolorer">
    $ curl http://val-eval-test.apigee.net/test<br />
    Hello, World! v0.10.32<br />
    $
  </div>
</div>

</pre>

&nbsp;

You may see the following error when accessing your endpoint using curl. This error usually occurs because it takes a little time for Apigee to finish deploying your API Gateway after the web interface says it is done. If you see this error, wait a couple minutes and try again.

&nbsp;

<pre><div class="codecolorer-container text default" style="overflow:auto;white-space:nowrap;width:435px;">
  <div class="text codecolorer">
    $ curl http://val-eval-test.apigee.net/test<br />
    {"fault":{"faultstring":"APIProxy revision 1 of test does not exist in environment test of organization val-eval","detail":{"errorcode":"messaging.runtime.ApplicationNotFound"}}}<br />
    $
  </div>
</div>

</pre>

&nbsp;

For more sophisticated Node.js applications you need to use Apigee&#8217;s <a href="https://www.npmjs.com/package/apigeetool" rel="nofollow">apigeetool library</a> to <a href="https://docs.apigee.com/api-services/content/deploying-standalone-nodejs-app" rel="nofollow">bundle your application.</a> Unfortunately, <a href="https://community.apigee.com/questions/48957/401-with-the-apigeetool.html" rel="nofollow">apigeetool</a>
is known for giving mysterious HTTP 401 errors with no further information</a>, so working with apigetool requires more sophistication.
  
  <p>
    &nbsp;
  </p>
  
  <h2>
    Express Serverless Platform and Express Gateway
  </h2>
  
  <p>
    In Express Serverless Platform, first create a new function and name it &#8216;myfunction&#8217;:
  </p>
  
  <p>
    &nbsp;
  </p><figure class="post-image">
  
  <img src="https://i.imgur.com/BpbxPAf.png" /></figure> 
  
  <p>
    &nbsp;
  </p>
  
  <p>
    Node.js functions in Express Serverless Platform have the same function signature as <a href="https://nodejs.org/api/http.html#http_event_request" rel="nofollow">native Node.js HTTP request listeners</a>. The function to print &#8216;Hello, world!&#8217; with Express Serverless Platform is shown below. Note that the exported function <strong>must</strong> have the same name as the function name you assigned in the Express Serverless Platform GUI.
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <div class="highlight highlight-source-js">
    <pre><span class="pl-c1">module</span>.<span class="pl-smi">exports</span> <span class="pl-k">=</span> {
  <span class="pl-en">myfunction</span> (<span class="pl-smi">req</span>, <span class="pl-smi">res</span>) {
    <span class="pl-smi">res</span>.<span class="pl-en">end</span>(<span class="pl-s"><span class="pl-pds">'</span>Hello, world!<span class="pl-pds">'</span></span>);
  }
};

</pre>
  </div><figure class="post-image">
  
  <img src="https://i.imgur.com/PhIgSoz.png" /></figure> 
  
  <p>
    Note that this function does not have to create an actual HTTP server. Express Serverless Platform handles creating a server for you, so you can write &#8220;serverless&#8221; functions without having to actually write an <a href="https://www.npmjs.com/package/express" rel="nofollow">express</a> application. You do still get access to the <a href="https://nodejs.org/api/http.html#http_class_http_serverresponse" rel="nofollow">Node.js HTTP response</a>, so you can set HTTP headers and set the <a href="https://en.wikipedia.org/wiki/List_of_HTTP_status_codes" rel="nofollow">HTTP status code</a>.
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    From the menu on the left, add a new gateway. This will add an <a href="http://www.express-gateway.io?utm_source=Comparison_GS_Apigee&utm_medium=blog&utm_campaign=2018-10-comparisons&utm_content=link">Express Gateway</a> instance to your project.
  </p>
  
  <p>
    &nbsp;
  </p><figure class="post-image">
  
  <img src="https://i.imgur.com/wrI1XHD.png" /></figure> 
  
  <p>
    &nbsp;
  </p>
  
  <p>
    Click the plus icon next to &#8220;Policies&#8221; to add a policy to the default <a href="https://www.express-gateway.io/docs/core-concepts#pipelines?utm_source=Comparison_GS_Apigee&utm_medium=blog&utm_campaign=2018-10-comparisons&utm_content=link" rel="nofollow">Express Gateway pipeline</a>. In Express Gateway, a pipeline is a sequence of <a href="https://www.express-gateway.io/docs/core-concepts#policies?utm_source=Comparison_GS_Apigee&utm_medium=blog&utm_campaign=2018-10-comparisons&utm_content=link" rel="nofollow">policies</a> for handling a request. Add an empty &#8216;proxy&#8217; pipeline.
  </p>
  
  <p>
    &nbsp;
  </p><figure class="post-image">
  
  <img src="https://i.imgur.com/j57NSfQ.png" /></figure> 
  
  <p>
    &nbsp;
  </p>
  
  <p>
    Drag a line from your gateway to your function, and Express Serverless Platform will automatically connect your proxy policy to your function.
  </p>
  
  <p>
    &nbsp;
  </p><figure class="post-image">
  
  <img src="https://i.imgur.com/DrlZzKe.png" /></figure> 
  
  <p>
    &nbsp;
  </p>
  
  <p>
    Express Serverless Platform will also create a function endpoint for you. Keep the &#8220;paths&#8221; for your function endpoint empty for now. Click on the &#8220;settings&#8221; icon to find the publicly accessible URL for your Express Serverless Platform project.
  </p>
  
  <p>
    &nbsp;
  </p><figure class="post-image">
  
  <img src="https://i.imgur.com/4B2sna1.png" /></figure> 
  
  <p>
    &nbsp;
  </p>
  
  <p>
    Running <a href="https://en.wikipedia.org/wiki/CURL" rel="nofollow">curl</a> on the URL will now run your custom function and give you the &#8220;Hello, world!&#8221; text.
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <pre>



<div class="codecolorer-container text default" style="overflow:auto;white-space:nowrap;width:435px;">
  <div class="text codecolorer">
    $ curl http://gateway-148-dev.lunchbadger.io<br />
    Hello, World!<br />
    $
  </div>
</div>

</pre>
  
  <h2>
    <a id="user-content-moving-on" class="anchor" href="https://gist.github.com/vkarpov15/62e14472915fe4f0964df81d5f3d122f#moving-on" aria-hidden="true"></a>Moving On
  </h2>
  
  <p>
    The combination of Express Serverless Platform and Express Gateway is a great alternative to Apigee for Node.js developers if you&#8217;re looking to leverage modern JavaScript. 
	&nbsp;
	In particular, Apigee requires you to use a version of Node.js that&#8217;s been deprecated for several years at the time of this writing. 
	&nbsp;
	Express Serverless Platform also allows you to simply write functions, rather than requiring you to build out a whole server application and then deploy it using an error-prone command line tool. Apigee is appealing if you want to deploy an existing Node.js application somewhere, or if you don&#8217;t want to use Node.js and just use their web GUI to configure your API Gateway. 
	&nbsp;
	However, the latter approach suffers from vendor lock-in, because you can&#8217;t simply take your API Gateway from Apigee&#8217;s GUI and run it locally or on a different cloud provider. 
	&nbsp;
	Express Serverless Platform&#8217;s GUI generates a git project for you, so you can clone your entire API Gateway stack, modify it in your preferred code editor, and run it locally or on your cloud provider of choice.
	&nbsp;
	
  </p>
  We’ve done up a detailed comparison analysis on features, pricing and more between Express Serverless Platform and Apigee Edge, which is available for download from our <a href="/resources/comparison-guides/" target="_blank">Resources page.</a>
  
  <p>
    Additionally, if you&#8217;re interested in more of these topics, join the live discussion on twitter <strong><a href="http://www.twitter.com/lunchbadger">@lunchbadger</a></strong> or <strong><a href="https://twitter.com/express_gateway">@express_gateway.</a></strong>
  </p>
  
  <hr/>
  
&nbsp;
&nbsp;

{{% button href="https://facebook.com/sharer/sharer.php?u=https%3A%2F%2Fexpress-serverless.io%2Fblog%2Fvs-apigee-features%2F" icon="fab fa-facebook" %}}Share{{% /button %}}

{{% button href="https://twitter.com/intent/tweet/?text=ESP%20vs%20Apigee%20Edge&amp;url=https%3A%2F%2Fexpress-serverless.io%2Fblog%2Fvs-apigee-features%2F" icon="fab fa-twitter" %}}Tweet{{% /button %}}

{{% button href="https://www.linkedin.com/shareArticle?mini=true&amp;url=https%3A%2F%2Fexpress-serverless.io%2Fblog%2Fvs-apigee-features%2F&amp;title=ESP%20vs%20Apigee%20Edge&amp;summary=ESP%20vs%20Apigee%20Edge&amp;source=https%3A%2F%2Fexpress-serverless.io%2Fblog%2Fvs-apigee-features%2F" icon="fab fa-linkedin" %}}Link{{% /button %}}
  
 


 [1]: https://docs.apigee.com/api-services/content/what-apigee-edge
 [2]: https://en.wikipedia.org/wiki/Apigee
 [3]: https://www.lunchbadger.com/express-serverless-platform/?utm_source=Comparison_GS_Apigee&utm_medium=blog&utm_campaign=2018-10-comparisons&utm_content=link
 [4]: https://github.com/nodejs/node/blob/master/doc/changelogs/CHANGELOG_V010.md#0.10.32
 [5]: https://github.com/nodejs/Release
 [6]: https://i.imgur.com/8T8BAOr.png
 [7]: https://i.imgur.com/doPOfwP.png
 [8]: https://i.imgur.com/NrT7Gk0.png
 [9]: https://i.imgur.com/p4Tkz2a.png
 [10]: https://i.imgur.com/Y0aMBps.png