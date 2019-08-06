---
title: ESP vs Google Cloud Functions
author: Valeri Karpov
description: A detailed getting started tutorial guide between Express Serverless Platform and Google Cloud Functions with examples by developers for developers.
weight: 2
type: post
date: 2018-05-01T17:04:42+00:00
url: /add-resource/hello-world-esp-vs-google-cloud-functions-example/
image: /uploads/2018/05/Hello-World_-in-LunchBadger-vs-Google-Cloud-Functions.png
um_content_restriction:
  - 'a:8:{s:26:"_um_custom_access_settings";s:1:"0";s:14:"_um_accessible";s:1:"0";s:19:"_um_noaccess_action";s:1:"0";s:30:"_um_restrict_by_custom_message";s:1:"0";s:27:"_um_restrict_custom_message";s:0:"";s:19:"_um_access_redirect";s:1:"0";s:23:"_um_access_redirect_url";s:0:"";s:28:"_um_access_hide_from_queries";s:1:"0";}'
categories:
  - Technology
tags:
  - Cloud Functions
  - Express Gateway pipeline.
  - express.js
  - Get Started with Google Cloud Functions
  - Get started with how to write custom functions
  - Get started with Node.js functions in LunchBadger
  - Google Cloud
  - Google Cloud Functions
  - "Google's cloud functions emulator"
  - LunchBadger GUI
  - minimal HTTP configuration
  - Node.js
  - Node.js function

---
[Google Cloud Functions][1] are [Google Cloud&#8217;s][2] equivalent to [AWS Lambda][3]. Like Lambda, Google Cloud Functions let you write custom functions and expose them via an HTTP interface through either Google Cloud Function&#8217;s minimal HTTP configuration or [Google Cloud Endpoints][4] for more sophisticated use cases. Express Serverless Platfom is a similar stack that lets you write Node.js APIs and expose those APIs through [Express Gateway][7] without vendor lock in. In this article, I&#8217;ll walk through setting up a rudimentary Node.js function in both Express Serverless Platform and Google Cloud, and discuss the tradeoffs of using one over the other.

## Get Started with Google Cloud Functions

Go to the [Google Cloud Functions landing page][1] and click **&#8220;Try it free&#8221;**. Google Cloud offers a free trial with $300 in credits for 1 year, which should be more than enough for this simple walkthrough.

&nbsp;<figure class="post-image">

![][8]</figure> 

&nbsp;

Click on the hamburger icon in the upper left and find the **&#8220;Cloud Functions&#8221;** link in the sidebar, then click **&#8220;Create function&#8221;**.

&nbsp;<figure class="post-image">

![][9]</figure> 

Name your function **&#8220;hello-world&#8221;** and leave the rest of the options in the **&#8220;Create function&#8221;** form unchanged. In particular, leave **&#8220;Function to execute&#8221;** as **&#8220;helloWorld&#8221;**, because that needs to match the name of the function your source code exports. Enter the below code as the source code for your function to print out the version of Node.js your cloud function is running on.

&nbsp;

<pre>exports.helloWorld = (req, res) =&gt; {
 res.send('Hello from Node.js ' + process.version);
 };</pre>

&nbsp;<figure class="post-image">

![][10]</figure> 

&nbsp;

Click **&#8220;Create&#8221;** and wait for Google to deploy your cloud function. It will take a few minutes, so you might take this time to check out Google&#8217;s [cloud functions emulator][11] that lets you run cloud functions locally and deploy them from the command line.

Once your function is deployed, click on it to display the function&#8217;s details.

&nbsp;<figure class="post-image">

![][12]</figure> 

&nbsp;

Click the **&#8220;Trigger&#8221;** tab to find your cloud function&#8217;s URL.

&nbsp;<figure class="post-image">

![][13]</figure> 

&nbsp;

Copy the URL and use [curl][14] to run your cloud function.

&nbsp;

<pre>$ curl https://us-central1-test21-201718.cloudfunctions.net/hello-world
 Hello from Node.js v6.11.5
 $

</pre>

Google Cloud Functions don&#8217;t give you any control over what version of Node.js you run, they run Node.js v6.11.5 currently and will upgrade when they upgrade. <a href="https://cloud.google.com/functions/docs/writing/#the_cloud_functions_runtime" target="_blank" rel="noopener noreferrer">Google&#8217;s stated policy</a> is to follow the Node.js LTS release schedule, but as of this writing they have not upgraded to Node.js 8.x despite it being an LTS release for 6 months.

## Express Serverless Platform and Express Gateway

In Express Serverless Platform, first create a new function and name it **&#8216;myfunction&#8217;**:

&nbsp;<figure class="post-image">

![][15]</figure> 

&nbsp;

Node.js functions in Express Serverless Platform have the same function signature as [native Node.js HTTP request listeners][16]. The function to print &#8216;Hello, world!&#8217; with Express Serverless Platform is shown below. Note that the exported function **\*\*must\*\*** have the same name as the function name you assigned in the Express Serverless Platform GUI.

&nbsp;

<pre>module.exports = {
 myfunction (req, res) {
 res.end('Hello, world!');
 }
 };
</pre>

&nbsp;<figure class="post-image">

![][17]</figure> 

&nbsp;

Note that this function does not have to create an actual HTTP server. Express Serverless Platform handles creating a server for you, so you can write **&#8220;serverless&#8221;** functions without having to actually write an [Express.js][18] application. You still get access to the [Node.js HTTP response][19], so you can set HTTP headers and set the [HTTP status code][20].

From the menu on the left, add a new gateway. This will add an [Express Gateway][7] instance to your project.

&nbsp;<figure class="post-image">

![][21]</figure> 

&nbsp;

Click the plus icon next to **&#8220;Policies&#8221;** to add a policy to the default [Express Gateway pipeline.][22] In Express Gateway, a pipeline is a sequence of [policies][23] for handling a request. Add an empty &#8216;proxy&#8217; pipeline.

&nbsp;<figure class="post-image">

![][24]</figure> 

&nbsp;

Drag a line from your gateway to your function, and Express Serverless Platform will automatically connect your proxy policy to your function.

&nbsp;<figure class="post-image">

![][25]</figure> 

&nbsp;

Express Serverless Platform will also create a function endpoint for you. Keep the **&#8220;paths&#8221;** for your function endpoint empty for now.

Click on the **&#8220;settings&#8221;** icon to find the publicly accessible URL for your Express Serverless Platform project.

&nbsp;<figure class="post-image">

![][26]</figure> 

Running [curl][14] on the URL will now run your custom function and give you the **&#8220;Hello, world!&#8221;** text.

&nbsp;

<pre>$ curl http://gateway-148-dev.lunchbadger.io
 Hello, World!
 $
</pre>

## 

## Moving On

The combination of Express Serverless Platform and Express Gateway is a great alternative to Google Cloud Functions if you&#8217;re looking to avoid vendor lock-in.

The Google Cloud Function emulator lets you develop locally and deploy to Google Cloud, but it only supports <a href="https://cloud.google.com/functions/docs/emulator" target="_blank" rel="noopener noreferrer">invoking functions from the command line</a>, so running a production application on the emulator isn&#8217;t a viable option.

On the other hand, Express Serverless Platform scaffolds out an app for you and stores it in a git repo that you can clone. That enables you to run your app locally or on any cloud provider. Express Serverless Platform does automatically host your app for you, but that isn&#8217;t your only option.

Google Cloud is appealing because Google is a well-established company with a proven track record of running sophisticated developer tools at massive scale. But using Google Cloud Functions means you must run your code on Google Cloud and manage your API using <a href="https://cloud.google.com/endpoints/" target="_blank" rel="noopener noreferrer">Google Cloud Endpoints</a>.

Furthermore, Google Cloud Functions have slightly different syntax than <a href="/add-resource/get-started-azure-functions-vs-express-serverless-platform-tutorial/" target="_blank">Azure Functions</a> or <a href="/add-resource/hello-world-esp-vs-ibm-cloud-functions-example/" target="_blank">IBM Cloud</a>, so switching cloud function providers requires significant refactoring.

&nbsp;

We&#8217;ve done up a detailed comparison analysis on features, pricing and more between Express Serverless Platform running on GCP compared to Google Cloud Functions, which you may download from our <a href="add-resource/pdf-guides/page/" target="_blank">Resources page.</a>


&nbsp;

Additionally, if you&#8217;re interested in more of these topics, join the live discussion on twitter **[@lunchbadger][27]** or **[@express_gateway.][28]**

&nbsp;
&nbsp;

{{% button href="https://facebook.com/sharer/sharer.php?u=https%3A%2F%2Fexpress-serverless.io%2Fadd-resource%2Fhello-world-esp-vs-google-cloud-functions-example%2F" icon="fab fa-facebook" %}}Share{{% /button %}}

{{% button href="https://twitter.com/intent/tweet/?text=ESP%20vs%20Google%20Cloud%20Functions&amp;url=https%3A%2F%2Fexpress-serverless.io%2Fadd-resource%2Fhello-world-esp-vs-google-cloud-functions-example%2F" icon="fab fa-twitter" %}}Tweet{{% /button %}}

{{% button href="https://www.linkedin.com/shareArticle?mini=true&amp;url=https%3A%2F%2Fexpress-serverless.io%2Fadd-resource%2Fhello-world-esp-vs-google-cloud-functions-example%2F&amp;title=ESP%20vs%20Google%20Cloud%20Functions&amp;summary=ESP%20vs%20Google%20Cloud%20Functions&amp;source=https%3A%2F%2Fexpress-serverless.io%2Fadd-resource%2Fhello-world-esp-vs-google-cloud-functions-example%2F" icon="fab fa-linkedin" %}}Link{{% /button %}}



 [1]: https://cloud.google.com/functions/
 [2]: https://cloud.google.com/
 [3]: https://aws.amazon.com/lambda/
 [4]: https://cloud.google.com/endpoints/
 [5]: https://www.lunchbadger.com/
 [6]: https://www.lunchbadger.com/express-serverless-platform/?utm_source=Comparison_GS_GC&utm_medium=blog&utm_campaign=2018-10-comparisons&utm_content=link
 [7]: http://www.express-gateway.io?utm_source=Comparison_GS_GC&utm_medium=blog&utm_campaign=2018-10-comparisons&utm_content=link
 [8]: https://i.imgur.com/lSzijLZ.png
 [9]: https://i.imgur.com/cVNm44O.png
 [10]: https://i.imgur.com/OpJymV1.png
 [11]: https://github.com/GoogleCloudPlatform/cloud-functions-emulator
 [12]: https://i.imgur.com/sRMnHMY.png
 [13]: https://i.imgur.com/r3rvHUy.png
 [14]: https://en.wikipedia.org/wiki/CURL
 [15]: https://i.imgur.com/BpbxPAf.png
 [16]: https://nodejs.org/api/http.html#http_event_request
 [17]: https://i.imgur.com/PhIgSoz.png
 [18]: https://www.npmjs.com/package/express
 [19]: https://nodejs.org/api/http.html#http_class_http_serverresponse
 [20]: https://en.wikipedia.org/wiki/List_of_HTTP_status_codes
 [21]: https://i.imgur.com/wrI1XHD.png
 [22]: https://www.express-gateway.io/docs/core-concepts#pipelines?utm_source=Comparison_GS_GC&utm_medium=blog&utm_campaign=2018-10-comparisons&utm_content=link
 [23]: https://www.express-gateway.io/docs/core-concepts#policies?utm_source=Comparison_GS_GC&utm_medium=blog&utm_campaign=2018-10-comparisons&utm_content=link
 [24]: https://i.imgur.com/j57NSfQ.png
 [25]: https://i.imgur.com/DrlZzKe.png
 [26]: https://i.imgur.com/4B2sna1.png
 [27]: http://www.twitter.com/lunchbadger
 [28]: https://twitter.com/express_gateway