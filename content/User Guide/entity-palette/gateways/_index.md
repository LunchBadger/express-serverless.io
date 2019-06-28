---
title: "Gateways"
weight: 50
date: 2018-05-21T18:37:58+03:00
draft: false
---

To create a Gateway click on the function icon on the entity palette: {{< figure src="/images/icon_gateway_dark.svg" style="float: right" height="50" width="50" >}}

The Gateway entity represents an instance of Express Gateway. Express Gateway is a microservices API Gateway.

In Express Serverless Platform, Gateways are used to provide API management functionality for your microservices application. A Gateway expose private and internal microservices publicly through APIs.

## How Gateways Work
Gateways in Express Serverless Platform are used to proxy to microservice entities in the private quadrant and manage and expose them as APIs as API endpoints in the public quadrant.

Each Gateway consists of one or more Pipelines. A Pipeline is a set of policies. Each Pipeline has connection ports to its left an right hand side.

The Models, Functions and Service Endpoints are proxied entities connected to the Gateway's Pipeline from the left hand side.

A corresponding API Endpoint in the public quadrant is created and connected to the right hand side of the Pipeline.

{{% notice info %}}
Gateways in Express Serverless Platform are powered by Express Gateway.  More details on Express Gateway can be found in the [Express Gateway Documentation](https://www.express-gateway.io/docs/)
{{% /notice %}}

## Walkthrough Example

![Gateway Example](/images/gateway_example.png)

A complete example microservice application is displayed in the Express Serverless Platform Canvas depicted above.

![Gateway Flow 1](/images/gateway_flow_1.png)

1. A TemperatureAPIEndpoint exists in the public quadrant. This API Endpoint is publicly accessible through HTTP.  You can cURL this endpoint through its URL.

    ```shell
    cURL http://<root url>/api/temperature
    ```

    ![Gateway Flow 2](/images/gateway_flow_2.png)

2. cURLing the API Endpoint sends the request to the Pipeline within the Gateway that is present in the Gateway quadrant.

    ![Gateway Flow 3](/images/gateway_flow_3.png)

3. The Pipeline contains a Proxy Policy which routes the request to the entity connected on its left hand port.

    ![Gateway Flow 4](/images/gateway_flow_4.png)

4. The Temperature Model is connected to the left hand port of the Pipeline and receives the request because of the Proxy policy within the Pipeline.

    ![Gateway Flow 5](/images/gateway_flow_5.png)

5. The Temperature Model is connected to the Memory Connector and the API Request to GET data.

    ![Gateway Flow 6](/images/gateway_flow_6.png)

6. The Temperature Model grabs temperature data from the Memory Connector populates a Temperature object through its Model definition with its properties and then sends that representation back through as the response.

## Accessing Gateway Instances
API Endpoints hosted by a Gateway iare accessible via URL and path(s) specified in the API Endpoint.

Example:

![Access Gateway](/images/gateway_access.png)

The CarAPIEndpoint depicted above is accessible through the URL - `http://gateway-al2-dev.staging.lunchbadger.io/api/car`

URLs for API Endpoints follow the convention listed below:

`http://<gateway root url>.lunchbadger.io/<api endpoint path>`



## Consumer Management
Gateways have a built in consumer management system as a reference implementation for identity management.
The purpose of consumer management is to define API Consumers that are known and managed by the Gateway.

![Consumer Management](/images/gw_consumer_mgmt.png)

Click on the man with the suitecase icon on the Gateway context toolbar to access Consumer Management

### API Consumers
An API Consumer is one of the following:

* User
* Application (App)

{{% notice info %}}
For more information on the Consumer Management capabilities within the Gateway, see the [Consumer Management](https://www.express-gateway.io/docs/consumer-management/) documentation on Express Gateway.
{{% /notice %}}

![Consumer Management Add User](/images/gw_cm_add_user.png)
To create Users,Apps, and Scopes press the plus `+` icon.

### Credentials
Every API Consumer has their own set of Credentials.  There are several types of Credentials supported by the Gateway in LunchBadger:

* basic authorization
* key authorization
* OAuth2

![Consumer Management Add User Credentials](/images/gw_cm_add_user_cred.png)
To create Credentials click on row of the User or App.

{{% notice info %}}
For more information on the Credentials supported bythe Gateway, see the [Credential Management](https://www.express-gateway.io/docs/credential-management/) documentation on Express Gateway.
{{% /notice %}}

Please refer to [Express Gateway Consumer Management](https://www.express-gateway.io/docs/consumer-management/) for more information
