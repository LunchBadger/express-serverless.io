---
title: "Cloud Runtime"
weight: 30
date: 2018-05-21T18:25:07+03:00
draft: false
---

One of the key advantages of what Express Serverless Platform brings is true cloud native freedom and choice.

Amazon Web Services Lambda and API Gateway, Azure Functions, Google Cloud Functions - do you like the productivity gains of what these cloud providers offer?

Express Serverless Platform gives you the same functionality with a **better** experience, complete transparency and control and allows you to run you microservices and serverless functions in any public or private cloud including your own datacenter.

{{% notice info %}}
When running Express Serverless Platform in your public cloud you can run serverless function in the public cloud's native serverless offering.  For example: running Express Serverless Platform on AWS means you can run serverless functions in AWS Lambda.
{{% /notice %}}

## Kubernetes
[Kubernetes](https://kubernetes.io) has become the common cloud substrate that allows you to run all containerized microservices based applications in the cloud.  All cloud providers either support Kubernetes as a direct cloud orchestration platform or are capable of running it on their barebone compute instances.

Kubernetes goes beyond containers.  Containers are the commonly accepted packaging of any application. Having containers isn't enough.

Microservices require many many container instances. A container orchestrator is require to tie all the microservices running in containers in a meaningful and practical way.

## Express Serverless Platform Makes Kubernetes Easy
Express Serverless Platform leverages Kubernetes as its cloud runtime.

{{% notice info %}}
All your microservices built within Express Serverless Platform are automatically built and packaged as containers and deployed into Kubernetes dynamically.
{{% /notice %}}

![Express Serverless Platform Canvas](/images/full_canvas.png)

When you are in the `development` environmnent building and configuring your microservices via the [Canvas](/user-guide/canvas)

![Kubernetes Pods](/images/kubernetes_pods.png)

... Express Serverless Platform is deploying them in real time to Kubernetes as [pods](https://kubernetes.io/docs/concepts/workloads/pods/pod/).

Once your microservices based application is complete and you are happy with its logical topology, **immutable** copies can be made into other Kubernetes environemnts like `staging`, `testing` and `production` etc.

### Canvas Microservices to Kubernetes Pod Mapping
Express Serverless Platform groups Canvas entities into separate pods running in Kubernetes.

Here is a table to understand what gets run as its own microservice as a pod in Kubernetes

Entity           | Kubernetes Pod Name | Notes
-----------------|---------------------|------
Models           | workspace           |  All Models and Connectors are in one LoopBack project running in one workspace pod
Connectors       | workspace           | (see note above)
Service Endpoint | gateway             | all Service Endpoints are linked to a Gateway and its correponding pod
Functions        | function            | 1 per Function Entity on the Canvas
API Endpoint     | gateway             | all API Endpoitns are linked to a Gateway and its correpsonding pod
Gateway          | gateway             | 1 per Gateway Entity on the Canvas

{{% notice info %}}
In the near future, Express Serverless Platform will allow you group individual Models that are related or have dependencies into a Microservice entity.  Microserivce entities will have their own pods in Kubernetes.
{{% /notice %}}

Example:

![Canvas To Pod Mapping](/images/canvas_to_pods.png)

Pod Breakdown in Kubernetes

* Blue - ONE workspace pod
* Green - TWO function pods, ONE for each individual Function
* Purple - ONE gateway pod
