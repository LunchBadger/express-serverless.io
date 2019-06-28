---
title: "About"
chapter: false
description: Express Serverless Platform is a MultiCloud Serverless Microservices Platform that provides a single pane of glass and cloud agnostic, portable canvas for building and deploying microservices.
weight: 5
date: 2018-05-18T15:18:39+03:00
draft: false
---

## What is Express Serverless Platform?
Express Serverless Platform enables developers to quickly write serverless functions and seamlessly deploy them as microservices through a secure API gateway using one intuitive visual interface. With Express Serverless Platform, you can:

- Easily build new microservices from scratch
- Quickly write new model functions and connectors to integrate microservices with legacy data and applications
- Streamline the development and deployment of serverless architecture
- Automatically implement industry-standard API gateway security

Express Serverless Platform is deployed on a Kubernetes runtime and ships with its own management utilities, making it easy to manage and scale on any private cloud, public cloud, or multi-cloud hybrid.

## Why would I want to use Express Serverless Platform?
**TIME.**

You'll save **massive** amounts of time trying to attain the benefits of a microservices architecture.  Express Serverless Platform provides the following to repeatedly save you time and build your microservices applications sustainably:

* best practices for microservices built into the tool
* cloud native separation of code, config and metadata
* code scaffolding and built-in boilerplates
* automated real time deployment to the cloud(s) of your choice
* visual orchestration and wiring of microservices to an API gateway, data sources, and more

By using Express Serverless Platform, you'll be building, revising and innovating your microservice based applications more quickly and predictably through its automation and enablement.

Example:

Getting your application into the cloud as a container is already hard enough.  Image now, deploying it to a container orchestrator and wiring it up to other dependent containers.

Express Serverless Platform containerizes your application for you.  It deploys an image to Kubernetes by creating the deployment and other complicated [YAML documents](https://github.com/kubernetes/examples/blob/master/guestbook/all-in-one/guestbook-all-in-one.yaml) for you and calls its [API](https://kubernetes.io/docs/concepts/overview/kubernetes-api/) rather than fumbling around with dozens of laborious [kubectl commands](https://kubernetes.io/docs/reference/kubectl/overview/).

## How does Express Serverless Platform Work?
Express Serverless Platform is driven by a GUI known as the [Canvas](/user-guide/canvas). The Canvas guides user in the process of building, deploying, and managing microservices and exposing them as APIs.

Express Serverless Platform utilizes the best of breed open source projects for easy adoption, constant innovation and specialization of what each component brings to putting together a holistic microservices platform.

Source-level access to these components provides opportunities in transparent customization and support along with community driven innovation.  Here are the main projects used behind the scenes and integrated into Express Serverless Platform:

- <a href="https://www.express-gateway.io" target="blank">Express Gateway</a> - an API gateway to expose microservices by defining them as service endpoints and exposing them as API endpoints externally
- <a href="https://loopback.io" target="blank">LoopBackJS</a> - a Node.js based framework that lets you create microservices using a model driven approach
- <a href="https://www.serverless.com" target="blank">Serverless</a> - a cloud agnostic framework that acts as an adapter to serverless (a.k.a  Function-as-a-Service (FaaS)) platforms.
- <a href="https://www.kubeless.io" target="blank">Kubeless</a> - a Kubernetes native serverless engine that allows you to write functions in many supported languages
- <a href="https://www.kubernetes.io" target="blank">Kubernetes</a>  - a container orchestrator that runs in any cloud that deploys microservices as they are built in LunchBadger
- <a href="https://reactjs.org" target="blank">ReactJS</a> - a GUI framework that allows you to extend and build on top of LunchBadger's visual interface

## What is Express Gateway?
Express Serverless Platform is built around another open source project, known as Express Gateway, which is a microservices and serverless API gateway built on ExpressJS.

If you’d like to learn more, please checkout the [Express Gateway website](https://www.express-gateway.io) and the [Github repository](https://github.com/expressgateway/express-gateway) or you can join the [Express Gateway Community](https://gitter.im/ExpressGateway/express-gateway) on Gitter.

## Need Support?
Now that you're armed with the basics of how to use Express Serverless Platform, have fun!  Feel free to play around with Entities on the Canvas and direct any questions to the Team via a [git issue](https://github.com/LunchBadger)
