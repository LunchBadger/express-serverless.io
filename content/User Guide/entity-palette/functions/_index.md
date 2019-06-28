---
title: "Functions"
weight: 30
date: 2018-05-21T18:37:43+03:00
draft: false
---

To create a Function click on the function icon on the entity palette: {{< figure src="/images/icon_function_dark.svg" style="float: right" height="50" width="50" >}}

The Function entity represents a serverless function that runs in the [Kubeless](https://kubeless.io) serverless engine in your Kubernetes cluster.

Serverless functions are self contained pieces of functionality that run when triggered.

When you create a new Function, you select the supported language to be used within the function and specify a name.  Once you create a function, it is automatically deployed.

{{% notice info %}}
What's the difference between Models and Functions?  Both Models and Functions are functions.  Models are Node.js only and have built in capabilites provided by the LoopBack framework. Functions are barebone functions that can be written in a number of supported languages through the Kubeless engine.
{{% /notice %}}

## Function Details
To enter code into the body of a Function, go to the Function Details by hovering over the title bar on the Function entity and click the ellipses icon on the context menu.

![Function Details Icon](/images/function_details_icon.png)

A code editor similar to the one provided in Model Details will be presented.

![Function Details](/images/function_details.png)

Node.js Example:

> `handler.js` is the file with main entry point. you can create another files and reference them

> `package.json` contains node.js package dependencies. Express Serverless Platform will install them during function launch.

 All Serverless Function code is stored in its own git repository. See [Git Access](/user-guide/git-access) for details.
