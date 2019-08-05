---
title: "Developer Guide"
menuTitle: Back End - Kube Watcher
description: Detailed developer guide for Express Serverless Platform back end.
chapter: false
weight: 5
date: 2018-05-21T18:23:50+03:00
draft: false
---

# kube-watcher

{{% button href="https://github.com/LunchBadger/kube-watcher" icon="fab fa-github-square" %}}Kube-watcher GitHub Repo{{% /button %}}

Watch Kubernetes resources with a resilient RxJS Observable client.
It is used buy UI to render deployemnt process of Functions and Gateways

implemented as https://github.com/LunchBadger/kube-watcher/blob/master/index.js

Let say you have `demo` user with ` dev` env 
access http://localhost:7788/channels/demo

you will get a stringified JSON 
{dev:  { gateway:{ gw-name: status}, workspace:{ws-name:status}}

```js
{
    "dev": {
        "gateway": {
            "gateway-demo-dev-gateway-696bb497cd-s7b6p": {
                "status": { running: true} 
            }
        },
        "workspace": {
            "workspace-demo-dev-87c8978b-6bmnw": {
                "status": { running: true} 
        }
    }
}
```
