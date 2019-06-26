---
title: ESP vs IBM Cloud Functions
author: Valeri Karpov
weight: 4
description: A detailed getting started tutorial guide between Express Serverless Platform and IBM Cloud Functions with examples by developers for developers.
type: post
date: 2018-04-03T12:31:41+00:00
url: /blog/hello-world-esp-vs-ibm-cloud-functions-example/
image: /uploads/2018/04/2.png
um_content_restriction:
  - 'a:8:{s:26:"_um_custom_access_settings";s:1:"0";s:14:"_um_accessible";s:1:"0";s:19:"_um_noaccess_action";s:1:"0";s:30:"_um_restrict_by_custom_message";s:1:"0";s:27:"_um_restrict_custom_message";s:0:"";s:19:"_um_access_redirect";s:1:"0";s:23:"_um_access_redirect_url";s:0:"";s:28:"_um_access_hide_from_queries";s:1:"0";}'
categories:
  - Technology
tags:
  - Bluemix
  - Express Gateway
  - express.js
  - How Do I Get Started with IBM Connect
  - IBM API Connect
  - Node.js
  - Node.js APIs
  - What are IBM Cloud Functions

---
<a href="https://www.ibm.com/cloud/functions" rel="nofollow">IBM Cloud Functions</a> are <a href="https://www.ibm.com/cloud/" rel="nofollow">IBM Cloud&#8217;s</a> equivalent to <a href="https://aws.amazon.com/lambda/" rel="nofollow">AWS Lambda</a>. Like Lambda, IBM Cloud Functions let you write custom functions and expose them via an HTTP interface through either IBM Cloud Function&#8217;s minimal HTTP configuration or <a href="https://www.ibm.com/cloud/api-connect" rel="nofollow">IBM API Connect</a> for more sophisticated use cases. Express Serverless Platform offers a similar stack that lets you write Node.js APIs and expose those APIs through [Express Gateway][2] without vendor lock in. In this article, I&#8217;ll walk through setting up a rudimentary Node.js function in both Express Serverless Platform and IBM Cloud, and discuss the tradeoffs of using one over the other.

&nbsp;

## <a id="user-content-ibm-cloud" class="anchor" href="https://gist.github.com/vkarpov15/a1c24e42dd7362ffefc9c6242242efbf#ibm-cloud" aria-hidden="true"></a>IBM Cloud

Go to <a href="https://console.bluemix.net/openwhisk/" rel="nofollow">IBM&#8217;s OpenWhisk landing page</a> and log in. IBM Cloud is the new name for what used to be called <a href="https://en.wikipedia.org/wiki/Bluemix" rel="nofollow">Bluemix</a>, so don&#8217;t be surprised by the bluemix.net URL.
 <a href="https://openwhisk.apache.org/" rel="nofollow">OpenWhisk</a> is an Apache open source project that provides the backbone for IBM Cloud Functions.

&nbsp;

Once you&#8217;ve logged in, click on the &#8220;Actions&#8221; tab on the left and then click &#8220;Create.&#8221;

&nbsp;

<a href="https://camo.githubusercontent.com/0b05f6a52aed4010649e27ace5c0481cd5261eb4/68747470733a2f2f692e696d6775722e636f6d2f623971703453372e706e67" target="_blank" rel="noopener noreferrer"><img src="https://camo.githubusercontent.com/0b05f6a52aed4010649e27ace5c0481cd5261eb4/68747470733a2f2f692e696d6775722e636f6d2f623971703453372e706e67" data-canonical-src="https://i.imgur.com/b9qp4S7.png" /></a>

&nbsp;

For this simple example, click on &#8220;Quickstart Templates&#8221; to get a list of ready-made &#8220;actions.&#8221; In OpenWhisk, an action is just another name for a function.

&nbsp;

<a href="https://camo.githubusercontent.com/da7e59ee303fc991afc74f8ad26c1e4d0cba1a37/68747470733a2f2f692e696d6775722e636f6d2f613863554b57442e706e67" target="_blank" rel="noopener noreferrer"><img src="https://camo.githubusercontent.com/da7e59ee303fc991afc74f8ad26c1e4d0cba1a37/68747470733a2f2f692e696d6775722e636f6d2f613863554b57442e706e67" data-canonical-src="https://i.imgur.com/a8cUKWD.png" /></a>

&nbsp;

Select the &#8220;Hello World&#8221; function template.

&nbsp;

<a href="https://camo.githubusercontent.com/0a0dde542115a5cc86564c579433fe4b7cd7ee6d/68747470733a2f2f692e696d6775722e636f6d2f4f3347306f4d682e706e67" target="_blank" rel="noopener noreferrer"><img src="https://camo.githubusercontent.com/0a0dde542115a5cc86564c579433fe4b7cd7ee6d/68747470733a2f2f692e696d6775722e636f6d2f4f3347306f4d682e706e67" data-canonical-src="https://i.imgur.com/O3G0oMh.png" /></a>

&nbsp;

The next step asks you for a package name, a runtime, and the actual code. A package is just a container for one or more cloud functions, potentially with shared configuration. IBM Cloud will fill in the form with package name &#8220;hello-world&#8221;, Node.js 8 as the runtime, and a simple &#8220;Hello World&#8221; function as the code, so you shouldn&#8217;t need to make any changes, just hit the &#8220;Deploy&#8221; button.

&nbsp;

<a href="https://camo.githubusercontent.com/068be3a9406ddacfe97f4c5b5f14bf25020599a3/68747470733a2f2f692e696d6775722e636f6d2f42374c4c5a4f542e706e67" target="_blank" rel="noopener noreferrer"><img src="https://camo.githubusercontent.com/068be3a9406ddacfe97f4c5b5f14bf25020599a3/68747470733a2f2f692e696d6775722e636f6d2f42374c4c5a4f542e706e67" data-canonical-src="https://i.imgur.com/B7LLZOT.png" /></a>

&nbsp;

Great, now you have your first cloud function. You can execute the function, but it is not accessible via HTTP. Click the &#8220;Endpoints&#8221; tab on the left to create an endpoint for this function.

&nbsp;

<a href="https://camo.githubusercontent.com/267e7a69a1532f8e2bf013b8f00b0074a7b8427a/68747470733a2f2f692e696d6775722e636f6d2f3452474a4d45702e706e67" target="_blank" rel="noopener noreferrer"><img src="https://camo.githubusercontent.com/267e7a69a1532f8e2bf013b8f00b0074a7b8427a/68747470733a2f2f692e696d6775722e636f6d2f3452474a4d45702e706e67" data-canonical-src="https://i.imgur.com/4RGJMEp.png" /></a>

&nbsp;

Now, click the &#8220;Enable as Web Action&#8221; checkbox to expose this action via REST API. A web action has a couple special properties as opposed to a regular action. First, a web action _must_ return an object that is serializable into JSON, or a [promise that resolves to such an object][3]. Second, if a web action returns an object that has a headers, statusCode or body property, OpenWhisk will use those properties to structure the HTTP response, rather than just stringifying the resulting JSON object.

&nbsp;

<a href="https://camo.githubusercontent.com/bbe4c955db68488a73f34cf4f1b2eaadc1a2c477/68747470733a2f2f692e696d6775722e636f6d2f68784b4b4a69442e706e67" target="_blank" rel="noopener noreferrer"><img src="https://camo.githubusercontent.com/bbe4c955db68488a73f34cf4f1b2eaadc1a2c477/68747470733a2f2f692e696d6775722e636f6d2f68784b4b4a69442e706e67" data-canonical-src="https://i.imgur.com/hxKKJiD.png" /></a>

&nbsp;

Once you&#8217;ve made your action into a web action, you should be able to access it via REST API. Click the copy icon in the &#8220;HTTP Method&#8221; panel to copy the URL for your function. You should then be able to use <a href="https://en.wikipedia.org/wiki/CURL" rel="nofollow">curl</a> to access your function via HTTP. Keep in mind IBM Cloud Functions do not have any authentication by default, so you don&#8217;t need any API key.

&nbsp;

<a href="https://camo.githubusercontent.com/0193b6917d985adc8d6a506a0ba0b24ecc3202e3/68747470733a2f2f692e696d6775722e636f6d2f706732776976342e706e67" target="_blank" rel="noopener noreferrer"><img src="https://camo.githubusercontent.com/0193b6917d985adc8d6a506a0ba0b24ecc3202e3/68747470733a2f2f692e696d6775722e636f6d2f706732776976342e706e67" data-canonical-src="https://i.imgur.com/pg2wiv4.png" /></a>

&nbsp;

Running curl on the URL will then execute your function and give you the result.

&nbsp;

<pre><div class="codecolorer-container text default" style="overflow:auto;white-space:nowrap;width:435px;">
  <div class="text codecolorer">
    $ curl https://openwhisk.ng.bluemix.net/api/v1/web/val%40karpov.io_dev/hello-world/helloworld.json<br />
    {<br />
    &nbsp; "greeting": "Hello stranger!"<br />
    }<br />
    $
  </div>
</div>

</pre>

## 

## <a id="user-content-lunchbadger-and-express-gateway" class="anchor" href="https://gist.github.com/vkarpov15/a1c24e42dd7362ffefc9c6242242efbf#lunchbadger-and-express-gateway" aria-hidden="true"></a>Express Serverless Platform and Express Gateway

In Express Serverless Platform, first create a new function and name it &#8216;myfunction&#8217;:

&nbsp;

<a href="https://camo.githubusercontent.com/b8e799e5084eecd2ed5e59a8637f97ba419cb4fc/68747470733a2f2f692e696d6775722e636f6d2f427062785041662e706e67" target="_blank" rel="noopener noreferrer"><img src="https://camo.githubusercontent.com/b8e799e5084eecd2ed5e59a8637f97ba419cb4fc/68747470733a2f2f692e696d6775722e636f6d2f427062785041662e706e67" data-canonical-src="https://i.imgur.com/BpbxPAf.png" /></a>

&nbsp;

Node.js functions in Express Serverless Platform have the same function signature as <a href="https://nodejs.org/api/http.html#http_event_request" rel="nofollow">native Node.js HTTP request listeners</a>. The function to print &#8216;Hello, world!&#8217; with Express Serverless Platform is shown below. Note that the exported function **must** have the same name as the function name you assigned in the Express Serverless Platform GUI.

&nbsp;

<div class="highlight highlight-source-js">
  <pre><span class="pl-c1">module</span>.<span class="pl-smi">exports</span> <span class="pl-k">=</span> {
  <span class="pl-en">myfunction</span> (<span class="pl-smi">req</span>, <span class="pl-smi">res</span>) {
    <span class="pl-smi">res</span>.<span class="pl-en">end</span>(<span class="pl-s"><span class="pl-pds">'</span>Hello, world!<span class="pl-pds">'</span></span>);
  }
};
</pre>
</div>

&nbsp;

<a href="https://camo.githubusercontent.com/eebad2fc2e2bd1180e9a341f36991fc6746e186f/68747470733a2f2f692e696d6775722e636f6d2f50684967536f7a2e706e67" target="_blank" rel="noopener noreferrer"><img src="https://camo.githubusercontent.com/eebad2fc2e2bd1180e9a341f36991fc6746e186f/68747470733a2f2f692e696d6775722e636f6d2f50684967536f7a2e706e67" data-canonical-src="https://i.imgur.com/PhIgSoz.png" /></a>

&nbsp;

&nbsp;

Note that this function does not have to create an actual HTTP server. Express Serverless Platform handles creating a server for you, so you can write &#8220;serverless&#8221; functions without having to actually write an <a href="https://www.npmjs.com/package/express" rel="nofollow">express</a> application. You do still get access to the <a href="https://nodejs.org/api/http.html#http_class_http_serverresponse" rel="nofollow">Node.js HTTP response</a>, so you can set HTTP headers and set the <a href="https://en.wikipedia.org/wiki/List_of_HTTP_status_codes" rel="nofollow">HTTP status code</a>.

From the menu on the left, add a new gateway. This will add an <a href="http://www.express-gateway.io?utm_source=Comparison_GS_IBM&utm_medium=blog&utm_campaign=2018-10-comparisons&utm_content=link" rel="nofollow">Express Gateway</a> instance to your project.

&nbsp;

<a href="https://camo.githubusercontent.com/057251058e4cb828664b45a42789682b4cf16d04/68747470733a2f2f692e696d6775722e636f6d2f777249315848442e706e67" target="_blank" rel="noopener noreferrer"><img src="https://camo.githubusercontent.com/057251058e4cb828664b45a42789682b4cf16d04/68747470733a2f2f692e696d6775722e636f6d2f777249315848442e706e67" data-canonical-src="https://i.imgur.com/wrI1XHD.png" /></a>

&nbsp;

Click the plus icon next to &#8220;Policies&#8221; to add a policy to the default <a href="https://www.express-gateway.io/docs/core-concepts#pipelines?utm_source=Comparison_GS_IBM&utm_medium=blog&utm_campaign=2018-10-comparisons&utm_content=link" rel="nofollow">Express Gateway pipeline</a>. In Express Gateway, a pipeline is a sequence of <a href="https://www.express-gateway.io/docs/core-concepts#policies?utm_source=Comparison_GS_IBM&utm_medium=blog&utm_campaign=2018-10-comparisons&utm_content=link" rel="nofollow">policies</a> for handling a request. Add an empty &#8216;proxy&#8217; pipeline.

&nbsp;

<a href="https://camo.githubusercontent.com/8bddf36779d88170c810f44ebfd6fd28adc359a0/68747470733a2f2f692e696d6775722e636f6d2f6a35374e5366512e706e67" target="_blank" rel="noopener noreferrer"><img src="https://camo.githubusercontent.com/8bddf36779d88170c810f44ebfd6fd28adc359a0/68747470733a2f2f692e696d6775722e636f6d2f6a35374e5366512e706e67" data-canonical-src="https://i.imgur.com/j57NSfQ.png" /></a>

&nbsp;

Drag a line from your gateway to your function, and Express Serverless Platform will automatically connect your proxy policy to your function.

&nbsp;

<a href="https://camo.githubusercontent.com/60e5536e92b8d6c1b7c73c7b8c21e2a56bf90eff/68747470733a2f2f692e696d6775722e636f6d2f44726c5a7a4b652e706e67" target="_blank" rel="noopener noreferrer"><img src="https://camo.githubusercontent.com/60e5536e92b8d6c1b7c73c7b8c21e2a56bf90eff/68747470733a2f2f692e696d6775722e636f6d2f44726c5a7a4b652e706e67" data-canonical-src="https://i.imgur.com/DrlZzKe.png" /></a>

&nbsp;

Express Serverless Platform will also create a function endpoint for you. Keep the &#8220;paths&#8221; for your function endpoint empty for now. Click on the &#8220;settings&#8221; icon to find the publicly accessible URL for your Express Serverless Platform project.

&nbsp;

<a href="https://camo.githubusercontent.com/593e0c211416de74d83559ccb476a2e67aaf8fb0/68747470733a2f2f692e696d6775722e636f6d2f344232736e61312e706e67" target="_blank" rel="noopener noreferrer"><img src="https://camo.githubusercontent.com/593e0c211416de74d83559ccb476a2e67aaf8fb0/68747470733a2f2f692e696d6775722e636f6d2f344232736e61312e706e67" data-canonical-src="https://i.imgur.com/4B2sna1.png" /></a>

&nbsp;

Running <a href="https://en.wikipedia.org/wiki/CURL" rel="nofollow">curl</a> on the URL will now run your custom function and give you the &#8220;Hello, world!&#8221; text.

&nbsp;

<pre><div class="codecolorer-container text default" style="overflow:auto;white-space:nowrap;width:435px;">
  <div class="text codecolorer">
    $ curl http://gateway-148-dev.lunchbadger.io<br />
    Hello, World!<br />
    $
  </div>
</div>

</pre>

## 

## Moving On

The combination of Express Serverless Platform and Express Gateway is a great alternative to IBM Cloud Functions if you&#8217;re looking to avoid vendor lock-in. IBM Cloud Functions are built on OpenWhisk, so in theory you should be able to migrate your IBM Cloud Functions deployment onto OpenWhisk, but IBM doesn&#8217;t provide any documentation on how to do that. On the other hand, Express Serverless Platform scaffolds out an app for you and stores it in a git repo that you can clone. That enables you to run your app locally or on any cloud provider. Express Serverless Platform does automatically host your app for you, but that isn&#8217;t your only option. IBM Cloud is appealing because IBM is a well-established company, but using IBM Cloud Functions means you must run your code on IBM Cloud and manage your API using <a href="https://www.ibm.com/cloud/api-connect" rel="nofollow">IBM API Connect</a>.

&nbsp;

We&#8217;ve done up a detailed comparison analysis on features, pricing and more between Express Serverless Platform running on IBM compared to IBM Cloud Functions, which is available for download from our <a href="/resources/comparison-guides/" target="_blank">Resources page.</a>

&nbsp;

Additionally, if you&#8217;re interested in more of these topics, join the live discussion on twitter **[@lunchbadger][4]** or **[@express_gateway.][5]**

&nbsp;
&nbsp;

{{% button href="https://facebook.com/sharer/sharer.php?u=https%3A%2F%2Fexpress-serverless.io%2Fblog%2Fhello-world-esp-vs-ibm-cloud-functions-example%2F" icon="fab fa-facebook" %}}Share{{% /button %}}

{{% button href="https://twitter.com/intent/tweet/?text=ESP%20vs%20IBM%20Cloud%20Functions&amp;url=https%3A%2F%2Fexpress-serverless.io%2Fblog%2Fhello-world-esp-vs-ibm-cloud-functions-example%2F" icon="fab fa-twitter" %}}Tweet{{% /button %}}

{{% button href="https://www.linkedin.com/shareArticle?mini=true&amp;url=https%3A%2F%2Fexpress-serverless.io%2Fblog%2Fhello-world-esp-vs-ibm-cloud-functions-example%2F&amp;title=ESP%20vs%20IBM%20Cloud%20Functions&amp;summary=ESP%20vs%20IBM%20Cloud%20Functions&amp;source=https%3A%2F%2Fexpress-serverless.io%2Fblog%2Fhello-world-esp-vs-ibm-cloud-functions-example%2F" icon="fab fa-linkedin" %}}Link{{% /button %}}



 [1]: https://www.lunchbadger.com/express-serverless-platform/?utm_source=Comparison_GS_IBM&utm_medium=blog&utm_campaign=2018-10-comparisons&utm_content=link
 [2]: http://www.express-gateway.io?utm_source=Comparison_GS_IBM&utm_medium=blog&utm_campaign=2018-10-comparisons&utm_content=link
 [3]: https://github.com/apache/incubator-openwhisk/blob/master/docs/actions.md#creating-asynchronous-actions
 [4]: http://www.twitter.com/lunchbadger
 [5]: https://twitter.com/express_gateway