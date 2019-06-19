---
title: "Entity Palette"
weight: 20
date: 2018-05-21T18:24:24+03:00
draft: false
---

The entity palette let's you create new entities onto the [Canvas](/basics/canvas) by simply clicking on the icon.  Entities are automatically created and placed into their corresponding [Quadrants](/basics/canvas/#quadrants).

Entity Types:

* Microservice Integration
* Microservice Composition
* API Management

## Microservice Integration Entities
If you have existing data or services that you want to leverage in your new microservies application, you can use these entities to leverage them.

Integration entities include:

* [Connectors](/basics/entity-palette/connectors) - let's you connect to data sources and existing services so that you can take advantage of them in a microservice built with a model

{{% notice tip %}}
[Model](/basics/models) entities can be connected to data sources and services through a Connector.
{{% /notice %}}

## Microservice Composition Entities
Composition entities let you build new microserivces with existing data and legacy applications or start greenfield often utilizing Connectors.

Composition entities include:

* [Models](/basics/entity-palette/models) - a prebuilt JavaScript function that represents an object with properties that can utilize Connectors
* [Functions](/basics/entity-palette/functions) - a serverelss function that can be written in Node.js, Go, Python, Ruby and other supported languages.

## API Management Entities

API Management entities include:

* [Gateways](/basics/entity-palette/gateways) - microgateways that function as an API Gateway that secures and manages your microservices and exposes them as consumable APIs
* [Service Endpoints](/basics/entity-palette/service-endpoints) - any internal endpoint that a Gateway proxies
* [API Endpoints](/basics/entity-palette/api-endpoints) - externalized endpoints that are exposed by the API Gateway to be consumed as an API by a client

{{% notice tip %}}
Everything proxied by a Gateway is technically considered a Service Endpoint.  A Service Endpoint is really nothing more than a referenced proxied URL. Models and Functions can be proxied by a Gateway and are seen as service endpoints to the Gateway because they automatically have HTTP based URLs assigned to them as microservices.
{{% /notice %}}
