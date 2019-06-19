---
title: "Model Connectors"
weight: 10
date: 2018-05-21T18:37:50+03:00
draft: false
---

To create a Model Connector click on the connector icon on the entity palette: {{< figure src="/images/icon_datasource_dark.svg" style="float: right" height="50" width="50" >}}
a sub-menu of different connector types will appear:

![Connector Submenu](/images/connector_submenu.png)

Model Connectors are prebuilt libraries that allow you to utlize a wide array of popular data sources and services.  At this time, Model Connectors can be only directly utilized by Models by connecting the Model Connector port to the left Model port.

![Model Connected to MySQL Connector](/images/model_connector_connection.png)

Each model connector entity will come with its own set of properties specific for that type of connection.

{{% notice info %}}
Model Connectors in Express Serverless Platform are based on [LoopBack data sources and their corresponding connectors](https://loopback.io/doc/en/lb3/Defining-data-sources.html)
{{% /notice %}}

Express Serverless Platform comes with the following connectors:

- Memory
- REST
- SOAP
- MongoDB
- Redis
- MySQL
- PostgreSQL
- Ethereum
- Salesforce
- Triton Object Storage

{{% notice info %}}
Express Serverless Platform provides a graphical interface for configuring the LoopBack based connectors listed above. Any LoopBack connector can be utilized by Express Serverless Platform.
There are many, many more LoopBack connectors that can be utilized by Express Serverless Platform even if there isn't a supporting GUI entry in Model Connectors entity types! Check out the [LoopBack Awesome List](https://github.com/pasindud/awesome-loopback) for more model connectors.
{{% /notice %}}
