---
title: "API Endpoints"
weight: 60
date: 2018-05-21T18:38:14+03:00
draft: false
---

To create an API Endpoint click on the endpoint submenu on the entity palette and choose the API endpoint icon: {{< figure src="/images/icon_endpoint_dark.svg" style="float: right" height="50" width="50" >}}

The API Endpoint Entity is an HTTP based URL that exposes a microservice proxied by the Gateway.

API Endpoints have two basic parts:

* a root URL
* path(s)

{{% notice tip %}}
API Endpoints can have multiple paths to support different URLs.
{{% /notice %}}

## Accessing an API Endpoint
To access an API Endpoint, the URL is a combination of the `root url` + the `path`.

Example:

![Access an API Endpoint](/images/gateway_access.png)

The CarAPIEndpoint depicted above has two parts:

* a root URL - `http://gateway-al2-dev.staging.lunchbadger.io`
* a path - `/api/car`

To access the CarEndpoint its complete URL is the following:

`http://gateway-al2-dev.staging.lunchbadger.io/api/car`

## API Endpoint Details
More advanced functionality can be accessed by accessing the API Endpoint Details by clicking the ellipses icon on the API Endpoint context toolbar.

### Methods
By default, API Endpoints are accessible by all HTTP verb methods:

* GET
* PUT
* POST
* DELETE
* PATCH
* OPTIONS
* HEAD
* TRACE
* CONNECT

If you want to limit the HTTP methods available to access the API Endpoint you can specify them here.

Example:

![API Endpoint Methods](/images/api_endpoint_details.png)

Only the GET method is supported by the Car API Endpoint shown above.  If you were to try to POST to this API Endpoint, you would receive a `401 Unauthorized` error.

### Scopes
Scopes are used to control authorization to the API Endpoint.  When an API Endpoint is access, its associated Scope is passed into the Gateway's Pipeline for evaluation. A Pipeline may utilize an authorization policy that can match the Scope against the API Consumer.

Example:

![API Endpoint Methods](/images/api_endpoint_details.png)

You are listed as an API Consumer as user `Bob`.  As `Bob`, you have a `basic authorization` credential specified a Scope of `read:user`.

You execute a GET on the Car API Endpoint shown above.

The `read:user` scope would be passed by the API Endpoint to the Pipeline hosted by the Gateway. A basic authorization policy is listed in the Pipeline.

The following authorization lookup is executed:

1. User `Bob` is looked up in the system
2. For user `Bob`, a basic authorization credential is checked
3. The basic authorization credentials is checked to make sure that a `read:user` is present
4. If the `read:user` scope is present, the API request is allowed, if it absent, then the API request is denied

{{% notice info %}}
For more information on Scopes, refer to the Scopes section in the [Credential Management](https://www.express-gateway.io/docs/credential-management/) documentation.
{{% /notice %}}
