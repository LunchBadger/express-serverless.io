---
title: "Git Access"
weight: 40
date: 2018-05-29T15:31:09+03:00
draft: false
---

All business functionality and custom code for your microservices are stored git repositories.

LunchBadger provide two Git repositories containing your project's code.

## Git Access to Your LunchBadger Project
In order to access git repositories within LunchBadger, you need to upload your public SSH key.

Access the Settings panel by clicking the cogs icon in the top right toolbar.

![Public Key](/images/public_keys.png)

Press `+` icon to add new SSH key

Example: Copying your SSH key to clipboard on macOS

To copy your `public` SSH key into the clipboard, open a Terminal window and run the following:

```shell
pbcopy < ~/.ssh/id_rsa.pub
```
![SSH settings](/images/settings_ssh_add.png)

Add a Label to identify the key in the future, paste the contents of your clipboard into the `Key` field, and click the `Upload` icon.

## Git Repository Access
Models and Connectors to data sources are enabled through [LoopBack](http://www.loopback.io).

Serverless Functions are enabled through [Kubeless](http://www.kubeless.io)

![Git Access URL](/images/git_access_url.png)

In the Settings panel, locate the `Access via Git` section.

## Git Repo Structures
Each Git reposistory has its own directory convention and structure.

### Model and Connectors
Models and Connectors are within the LoopBack project directory structure.

{{% notice info %}}
Refer to the [LoopBack project layout reference](https://loopback.io/doc/en/lb3/Project-layout-reference.html) for more in-depth information about the LoopBack project
{{% /notice %}}

The Model JSON based schema and JavaScript files can be found in the `server/models` directory once you clone the repository for Models and Connectors.

### Functions
The Functions repository contains a subdirectory for each folder by Function name.

Example:

If you have a Function on the Canvas named `PriceCalculator`, you will have a corresponding top level subdirectory with the same name with all the files related to the Function.  The main file for Functions is often the `handler.js`


{{% notice info %}}
For more information on how to structure the code for you serverless Functions refer to the [Runtime reference](https://kubeless.io/docs/runtimes/) in the Kubeless documentation.
{{% /notice %}}

