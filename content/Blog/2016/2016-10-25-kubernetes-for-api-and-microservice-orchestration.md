---
title: Kubernetes for API and Microservice Orchestration
author: Roman Lisagor
type: post
date: 2016-10-25T16:51:20+00:00
url: /blog/kubernetes-for-api-and-microservice-orchestration/
featured_image: /uploads/2016/10/Top-3-Tips-to-Understanding-API-User-Experience-4.png
categories:
  - Technology
tags:
  - container management
  - Docker
  - Kubernetes
  - Mesosphere
  - orchestrator
  - Swarm

---
Two weeks ago, we talked about the [benefits that Docker brings][1] to organizations building out an API infrastruture. Last week, we went one level higher to look at [how container orchestrators promise to simplify the deployment and management of applications and APIs][2]. This week, I&#8217;ll describe a more personal perspective &#8211; why we chose Kubernetes as our container orchestrator.

The decision came down to three major reasons: community, ease of use, and feature set.

&nbsp;

## Community

While Mesos/Marathon is the oldest and most mature of the three solutions we discussed last time (the others being Kubernetes and Docker Swarm), Kubernetes is by far the most popular solution today. The community around this project from Google has grown extremely quickly. Here&#8217;s a quick comparison of some basic metrics of the three communities:

  * Kubernetes 38000 commits, 940 contributors, 4500 issues
  * Mesos/Marathon: 4800 commits, 217 contributors, 655 issues
  * Swarm: 3200 commits, 153 contributors, 288 issues

These metrics are definitely not scientific, but still provide a rough idea of the magnitude of work going into these projects. Kubernetes outstrips the competition by an order of magnitude.

&nbsp;

## Ease of use and installation

This was relatively important for us. With a small technical team, we don&#8217;t have a lot of time to tackle complex procedures. On this point, Kubernetes is actually middle of the pack due to its somewhat sophisticated architecture. For installation, we ended up using the [kube-aws tool from CoreOS][3] to get us started. This tool generates CloudFormation templates. Shortly thereafter, though, we moved from CloudFormation to Terraform. This is mostly preference, but does make infrastructure management a little easier.

The Kubernetes team seems to be aware of this potential roadblock to adoption; and, in version 1.4, [a new tool (kubeadm) has shipped][4] that makes it easier to set up Kubernetes clusters. This is a welcome step forward; I look forward to seeing this tool grow and evolve.

After it is installed, using Kubernetes to deploy and manage containers is a cinch. The _kubectl_ CLI tool is very easy to understand and set up on your machine. Resources are defined declaratively as YAML or JSON files and pushed into the cluster. Kubernetes takes over from there.

Mesos/Marathon is a bit more difficult to install, because the batteries are not included. As a result, additional pieces, such as RexRay and marathon-lb need to be installed as well. This increases complexity overall.

Docker Swarm gets you to a base installation very quickly. It ships automatically with every Docker Engine installation. The Swarm is managed via the same _docker_ CLI that engineers are already used to. As a result, it is probably the easiest to use of the three. However, some features are still missing and must be filled in with 3rd party software.

&nbsp;

## Features

This is the biggest draw towards Kubernetes. With this project, Google are successfully building a batteries-included &#8220;works out of the box&#8221; solution. The does come at a cost of some flexibility, but so far it has worked really well for our use case.

Pretty well every feature we could conceive of or problem we encountered is either already in beta, has a workaround, or is being somehow addressed in Github&#8217;s issue tracker. This is a very reassuring sign when dealing with cutting edge technology. In particular, many of the items we discussed in the previous blog post have mainstream solutions in the Kubernetes ecosystem:

  * Storage (persistent volumes / AWS EBS volume management)
  * Configuration
  * Secrets
  * Load balancing
  * Service discovery
  * Flexible scheduling policy

&#8230; and many more.

&nbsp;

## Conclusion

Of the three orchestrators we considered, we have found Kubernetes to be the closest to a feature-complete turn-key solution. The ecosystem around it is the largest of the three, and growing rapidly. While ease of installation does leave much to be desired, this is already being addressed and is something we can live with.

Docker Swarm is the youngest contender for this market, and is following in Kubernetes&#8217; footsteps. Many features clearly take inspiration from their Kubernetes analogs. If they are successful at building out their feature set, they could gain a leg up in this space over the coming months and years. Docker has a major advantage: Docker Engine is ubiquitous and now ships with Docker Swarm built in.

Mesos/Marathon is the most mature and flexible solution; however, it is also the most complex. If you are a larger entreprise with a wide range of use cases, you should probably consider this option more seriously.

* * *

Please check out LunchBadger for more information on how we’re using Kubernetes to empower companies to compose, manage, monitor, and monetize their APIs:

  * Check out the [demo][5] to see how LunchBadger provides a Docker container based runtime for APIs that works natively in your cloud and also harnesses the simplicity of a serverless experience.
  * Read about the [features][6] modeled after the API lifecycle as a solution from start to end, all on the same Docker container runtime.
  * Become an early participant to realize the simplicity and speed of having APIs work for you and your business.
  * For more information please contact us at <admin@express-serverless.io>.

 [1]: https://www.lunchbadger.com/docker-four-benefits-for-apis/
 [2]: https://www.lunchbadger.com/container-orchestration-apis-microservices/
 [3]: https://coreos.com/kubernetes/docs/latest/kubernetes-on-aws.html
 [4]: http://blog.kubernetes.io/2016/09/kubernetes-1.4-making-it-easy-to-run-on-kuberentes-anywhere.html
 [5]: https://www.express-serverless.io/getting-started/
 [6]: https://www.express-serverless.io/getting-started/
