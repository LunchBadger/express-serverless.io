---
title: Leveraging Kubernetes For Microservices Based Cloud Strategy
menuTitle: Leveraging Kubernetes
author: Al Tsang
type: post
date: 2018-08-13T19:26:15+00:00
url: /blog/kubernetes-scalability/
image: /uploads/2018/08/Trial-3.png
um_content_restriction:
  - 'a:8:{s:26:"_um_custom_access_settings";s:1:"0";s:14:"_um_accessible";s:1:"0";s:19:"_um_noaccess_action";s:1:"0";s:30:"_um_restrict_by_custom_message";s:1:"0";s:27:"_um_restrict_custom_message";s:0:"";s:19:"_um_access_redirect";s:1:"0";s:23:"_um_access_redirect_url";s:0:"";s:28:"_um_access_hide_from_queries";s:1:"0";}'
categories:
  - Featured
  - Technology
tags:
  - auto deployment in a kubernetes runtime
  - command-line tool called kubectl for deploying containerized applications and managing services
  - How to get started with Kubernetes
  - Kubectl
  - Kubernetes
  - Kubernetes Pod
  - Kubernetes Runtime

---
<span style="font-weight: 400;">Enterprise applications have to be designed upfront for <strong>scalability and change</strong>. This has significant implications for both application architecture and application infrastructure. Application architecture is evolving from unmanageable monolithic or three-tier patterns to interconnected microservices.</span> [<span style="font-weight: 400;">Microservices</span>][1] <span style="font-weight: 400;">introduce new form factors not only for functionality and team-size (the so-called two-pizza teams), but also for the unit of infrastructure. It is not surprising that a portable container or a pod of handful interrelated containers often works out as the most befitting unit of infrastructure for microservices-based architecture. </span><span style="font-weight: 400;">Fortunately, container-based scalable infrastructure is a reality today, thanks to the</span> [<span style="font-weight: 400;">Kubernetes</span>][2] <span style="font-weight: 400;">project incepted in and open-sourced by</span> [<span style="font-weight: 400;">Google</span>][3] <span style="font-weight: 400;">in 2014. But for the sake of business agility, it is critical for enterprise development teams to focus on the business logic with the insurance that deployment onto a suitable infrastructure would be relatively painless.</span>

## How LunchBadger integrates with Kubernetes

&nbsp;

<span style="font-weight: 400;">This is where LunchBadger comes in. LunchBadger offers a visual interface called the Canvas to model and define services, and deploy them onto a Kubernetes-based infrastructure in a single pane of glass. These services could be business-to-business services or intra-organization, or even intra-application microservices. They could be synchronously invoked</span> [<span style="font-weight: 400;">REST</span>][4] <span style="font-weight: 400;">URLs or asynchronously invoked serverless functions. In any case, it allows the developer to focus on application development and deploy the application onto a scalable Kubernetes-based infrastructure without any administrative intervention. LunchBadger is a Kubernetes-native solution such that the application developer does not switch from the Canvas, even as the requisite container instances are created and orchestrated behind the scene. So, let&#8217;s take a tour of life without LunchBadger &#8211; how it takes a sequence of steps to deploy and expose a service on a Kubernetes cluster &#8211; and then explore how LunchBadger cuts down the complexity to a one-click deployment.</span>

&nbsp;

## **Kubernetes In A Nutshell**

<span style="font-weight: 400;">Kubernetes is an deployment and orchestration framework for containerized applications. Given a farm of compute resources, Kubernetes allocates resources to containers and performs replication, scaling, failover, and other management tasks necessary to run enterprise applications reliably with efficient resource utilization.</span>

&nbsp;

<span style="font-weight: 400;">Datacenters that run applications on virtualization technologies like VMWare depend on a suite of tools like</span> [<span style="font-weight: 400;">VSphere</span>][5] <span style="font-weight: 400;">to deploy and manage Virtual Machines on a server farm. Kubernetes plays a similar role in the world of containerized applications.</span>

&nbsp;

<span style="font-weight: 400;">The unit of deployment in Kubernetes is a &#8216;pod&#8217;. A</span> [<span style="font-weight: 400;">Pod</span>][6] <span style="font-weight: 400;">consists of one a small number of containers that are deployed and scaled together as a unit. A cluster consists of Nodes, which are compute resources that can join or leave a cluster. Pods can be deployed onto a running cluster using a </span>[<span style="font-weight: 400;">deployment</span>][7] <span style="font-weight: 400;">specification. Among other attributes, a deployment spec includes the desired state of the cluster in terms of number of replicas of a pod that should be running at any point in time. The run-time ensures that the desired number of replicas are always maintained, even if one or more pods crash.  Secondly, a deployment spec can be used to run rolling upgrades on the specified pods. </span>

&nbsp;

<span style="font-weight: 400;">Finally, Kubernetes defines &#8216;</span>[<span style="font-weight: 400;">Service</span>][8]<span style="font-weight: 400;">&#8216; as a location-independent abstraction of the server processes running within pods. That is, while the pods may be allocated to different compute resources at different times based on availability, the service endpoint remains unchanged, so that it can be discovered and accessed externally without any disruption.</span>

&nbsp;

<span style="font-weight: 400;">Kubernetes also comes with a command-line tool called</span> [<span style="font-weight: 400;">kubectl</span>][9] <span style="font-weight: 400;">for deploying containerized applications and managing services.</span>

&nbsp;

_Let&#8217;s break it down:_<figure class="post-image">

<img class="aligncenter wp-image-4847" src="/wp-content/uploads/2018/08/Container.png" alt="Overview of Kubernetes" width="755" height="378" srcset="/wp-content/uploads/2018/08/Container.png 1024w, /wp-content/uploads/2018/08/Container-300x150.png 300w, /wp-content/uploads/2018/08/Container-768x384.png 768w, /wp-content/uploads/2018/08/Container-225x113.png 225w, /wp-content/uploads/2018/08/Container-512x256.png 512w" sizes="(max-width: 755px) 100vw, 755px" /></figure> 

&nbsp;

### **How Kubernetes, Microservices And Serverless work together**

<span style="font-weight: 400;">Martin Fowler lists out a few</span> [<span style="font-weight: 400;">characteristics of Microservices architecture</span>][1]<span style="font-weight: 400;">, two of which may be worth calling out here:</span>

&nbsp;

  1.  <span style="font-weight: 400;">    Componentization via Services</span>
  2. <span style="font-weight: 400;">    Smart Endpoints and &#8220;dumb pipes&#8221;</span>

&nbsp;

<span style="font-weight: 400;">Kubernetes is uniquely positioned to be the deployment platform of choice for Microservices. The &#8216;components&#8217; of a microservices-based application can be developed, built, tested, deployed and scaled independently. Kubernetes uses containers, and containers enable application components to be portable and easily integrated in a larger application.</span>

&nbsp;

<span style="font-weight: 400;">In event-driven scenarios, traditionally, enterprise service bus or similar technologies have been used to process message streams and trigger workflows. In microservices, the preference is to reduce complexity of the pipeline between application components, because otherwise the pipeline itself tends to become a monolithic component that has to be deployed and managed separately. Event driven microservices can be deployed as</span> [<span style="font-weight: 400;">serverless</span>][10] <span style="font-weight: 400;">functions. </span>

&nbsp;

<span style="font-weight: 400;">With Kubernetes-native serverless frameworks like</span> [<span style="font-weight: 400;">kubeless</span>][11]<span style="font-weight: 400;">, Kubernetes is capable of  serving as the deployment infrastructure for event-driven microservices as well.</span>

&nbsp;<figure class="post-image">

<img class="aligncenter wp-image-4848" src="/wp-content/uploads/2018/08/Container-1.png" alt="Deployment infrastructure for event-driven microservices" width="693" height="347" srcset="/wp-content/uploads/2018/08/Container-1.png 1024w, /wp-content/uploads/2018/08/Container-1-300x150.png 300w, /wp-content/uploads/2018/08/Container-1-768x384.png 768w, /wp-content/uploads/2018/08/Container-1-225x113.png 225w, /wp-content/uploads/2018/08/Container-1-512x256.png 512w" sizes="(max-width: 693px) 100vw, 693px" /></figure> 

<span style="font-weight: 400;">Microservices components &#8211; event-driven or otherwise, have to expose an interface for other components or the external world to access its services. This is where APIs have to be carefully defined, and an infrastructure for setting up and managing secure API endpoints has to be supported. </span><span style="font-weight: 400;">LunchBadger brings together a development platform for microservices &#8211; both synchronous and event-driven (serverless) &#8211; with an API management framework, with end-to-end development and deployment support.  </span>

&nbsp;

Over the next few posts, we&#8217;ll cover tactical examples, guides and walk through how-tos so you can deploy a service in Kubernetes, understand and create a Kubernetes deployment spec, understand and create a Kubernetes Service Spec or just what Kubernetes is all about.

&nbsp;

**Next Post:**

 [1]: https://www.martinfowler.com/articles/microservices.html
 [2]: https://kubernetes.io/
 [3]: https://www.google.com/about/
 [4]: https://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm
 [5]: https://www.vmware.com/in/products/vsphere.html
 [6]: https://kubernetes.io/docs/concepts/workloads/pods/pod/
 [7]: https://kubernetes.io/docs/concepts/workloads/controllers/deployment/
 [8]: https://kubernetes.io/docs/concepts/services-networking/service/
 [9]: https://kubernetes.io/docs/reference/kubectl/overview/
 [10]: https://serverless.com/
 [11]: https://github.com/kubeless/kubeless