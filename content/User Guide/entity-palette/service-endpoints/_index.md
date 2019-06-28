---
title: "Service Endpoints"
weight: 40
date: 2018-05-21T18:38:14+03:00
draft: false
---

To create a Service Endpoint click on the endpoint submenu on the entity palette and choose the service endpoint icon: {{< figure src="/images/icon_endpoint_dark.svg" style="float: right" height="50" width="50" >}}

The Service Endpoint Entity is a simple generic HTTP based resource with a URL.

Gateways in LunchBadger are Express Gateway instances. A Service Endpoint in Express Gateway is any resource that the gateway proxies in front of.

{{% notice info %}}
Models and Functions have HTTP URls pointing to them as HTTP based microservices. When you connect a Model or Function to a Gateway, a service endpoint is declared behind the scenes in Express Gateway to point to the HTTP URL of the Model or Function.
{{% /notice %}}
