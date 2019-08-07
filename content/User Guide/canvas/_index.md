---
title: "Canvas"
weight: 10
date: 2018-05-21T18:25:07+03:00
draft: false
---

{{% notice info %}}
Within Express Serverless Platform, the Canvas is a single pane of glass where you can create, build, and deploy your microservices and APIs.
{{% /notice %}}


![Express Serverless Platform Canvas Image](/images/full_canvas.png)

The Canvas is broken up into a few easy parts to understand:

* header
* entity palettte
* quadrants
* toolbar
* panels
* chat

### Header

![Header](/images/header.png)
The information displayed at the very top of the Canvas is called the Header.  The Header contains information about the current state of the Canvas, starting from left to right:

* username
* environment name
* project name

{{% notice info %}}
At this time, all environments are limited to `dev(elopment)` environments within the online trial and a single project called `Canvas` by default.
{{% /notice %}}

Each Canvas is uniquely made up of a user, environment and project.

### Entity Palette

![Entity Palette](/images/entity_palette.png)
The left most toolbar is called the Entity Palette.  Each icon in the palette represents a different entity that you can create.  The entity palette is divided up into different entity types.

Some entities are used when you are developing your microservcies and integrating to existing data and application. Others are used when you want to expose microservices as APIs and secure them through an API gateway.
More Details:  [Entity Palette](/user-guide/entity-palette)

### Quadrants

![Quadrants](/images/quadrants.png)
The columns that take up most of the area witihn the Canvas with a gray header are called Quadrants. Quadrants represent different tiers within your microservices application. They are designed to help you logically classify the different parts of your application in a microservices architecture. Having the logical model of your microservices defined makes it easier to scale individual microservices accordingly within the Kubernetes runtime.

#### Backend
The backend quadrant represents where you data and services exist and or persisted.  Microservices can be built on top of existing legacy applications and or data.

{{% notice tip %}}
There's no need to throw away your old applications as you move into a microservices architecture. Express Serverless Platform has tooling to help you create a new layer of microservices on top of your legacy applications and data. This will allow you to build entirely new microservices alongside microservices that sit as a layer on top of what already exists.
{{% /notice %}}

Express Serverless Platform utilizes the same tooling to connect to new data sources where you want to persist data utilized with new microserivces.

Example: Legacy Data in MySQL

> You have data in MySQL that exists as rows and tables and you want to create a set of microservices that represent that data. A MySQL Connector can be created in the backend quadrant and represents a connection to MySQL as a legacy data source.

Example: New Data to be stored in MongoDB

> You are creating a new microservice that handles payments.  The microservices requires each payment performed to be recorded with transaction details as a JSON object. A MongoDB Connector can be created in the backend quadrant that represents the connection to new MongoDB instance that will store the new transaction data.

#### Private
The private quadrant represents all business functionality within your application.  This quadrant contains all [Models](/user-guide/entity-palette/models), [Service Endpoints](/user-guide/entity-palette/service-endpoints) and [Functions](/user-guide/entity-palette/functions) in your system. They are not exposed publically, but can communicate with each other. In Express Serverless Platform communication with external services is done through a [Gateway](/user-guide/entity-palette/gateways)

Example: Legacy SOAP Service Leveraged by New Customer Model Microservice

> You have a legacy SOAP service that represents a customer.  The customer SOAP object has 100 properties. You want to surface a new credit application API backed by a Model based microservice that only requires 10 of the 100 fields that are minimally needed for a new customer applying for credit.  A customer microsevice Model can be created with the 10 fields that are required connecte to an instance of the SOAP Connector in the backend quadrant pointed to the legacy SOAP service.

Example: Serverless Function

> You have a function that calculates and suggests a recommended price for a particular car given an historical list of average prices and dates paid by past buyers for the car. A SuggestedPriceCalculator Function can be deployed and written in Node, Python and other languages to take the list of average prices and dates and do a weighted calcuation of a price to look for when shopping for a car.

Example: Barebone Service Endpoint Proxing an External Service

> You want to surface a uniform API that powers a Yelp like application that shows all restaurants near your user.  The list of restaurants and their addresses are handled by a Restaurant model based microservice and the geolocation lookup is done by a 3rd party API - Google Maps.  A Service Endpoint can be created to point to the Google Maps URL to pass in geolocation coordinates to do a lookup calculation for distance between the user and each of the restaurants.

#### Gateway
The gateway quadrant is a dividing line between what is public facing and consumed by consumers through an API and what is private and managed by producers as a set of microservices connected to backend systems. The only entity created within this quadrant are gateways. [Gateway Entities](/user-guide/entity-palette/gateways) represent created and deployed instances of Express Gateway. These instances act as an API Gateway within your application. Gateways expose HTTP based API endpoints, provide policy based quality of services (like routing, authentication, authorization, rate-limiting etc.) and proxy in front of entities within the private quadrant.

Example:

> You have a couple of Model based microservices that act as REST resources - cart, catalog, user. Each of these Models can be wired up to a Gateway entity in this quadrant and be exposed as REST API endpoint by the gateway. The Gateway in this quadrant can be configured with policies to proxy to these backend Models and secure them with authentication and authorization policies like key authorization.

#### Public
The public quadrant contains entities that are exposed and directly visible to any consumer of your application. Consumers can interact directly with these entities. The public quadrant contains [API Endpoint entities](/user-guide/entity-palette/api-endpoints) exposed by Gateways in the gateway quadrant. API Endpoints are HTTP based URLs that can be called directly by a client external to your application.

Example:

> You have a domain and URL for exposing a REST API for cart as http://<span></span>www.petstore.com/api/v1/cart. This URL is exposed as an API Endpoint in the public quadrant.

### Toolbar
![Toolbar](/images/toolbar.png)

The top right hand icon menu is known as the Toolbar.   The Toolbar displays various utilities that can be invokved including Panels (see below)

The following are the icons on the Toolbar:

* trash can - clear entire Canvas (use this caution!)
* gear - Settings Panel
* question mark - documenation
* power icon - logout

### Panels
![Panel](/images/panels.png)
Panels are different views within Express Serverless Platform. Panels are featured alongside other icons on the top right toolbar in the header within the user interface.  Each panel slides down the quadrants from sight partially to review a new panel of controls.  The Settings Panel featured by the cogs icon is the only panel available at this time.

![Panel](/images/panels.png)

### Chat
![Chat](/images/chat.png)

If you need help at any time, you can click on the Chat icon to contact the team at LunchBadger. Chat supports both live messaging and can leave messages asynchronously so you can always be assured that you'll be heard and get a response.
