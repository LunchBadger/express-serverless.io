---
title: "Models"
weight: 20
date: 2018-05-21T18:37:43+03:00
draft: false
---

To create a Model click on the model icon on the entity palette: {{< figure src="/images/icon_model_dark.svg" style="float: right" height="50" width="50" >}}

The Model Entity is a graphical representation of a [LoopBack Model](https://loopback.io/doc/en/lb3/Defining-models.html).  Models can have properties you'd like to expose from data sources and services through [Connectors](/basics/entity-palette-connectors).

{{% notice info %}}
If you're familiar with the [Model-View-Controller pattern](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller), Models in Express Serverless Platform are exactly the `M` in `MVC`. For folks who are more backend, a model is very much like a [data access object](https://en.wikipedia.org/wiki/Data_access_object).
{{% /notice %}}

All Models are Node.js JavaScript functions. Models have the following basic built in functionality:

* properties
* read and or write data through [Connectors](/basics/connectors).
* scaffold a REST representation dynamically based on its definition

## Quick Edit a Model
After creating a Model in the [private quadrant](/basics/canvas/#private), you'll be ready to enter properties with a property name and property type while in **Quick Edit** mode.
To enter quick edit mode for a Model, click the pencil **Quick Edit** icon on the Model, by hovering over its title bar to display the context menu.

![Model Quick Edit Icon](/images/model_qedit_icon.png)

## Model Details
Models have advanced functionality that can be access through its **Details**.  To access a Model's **Details**, hover over the title bar to display the context menuu and chose the ellipses icon.

![Model Details Icon](/images/model_details_icon.png)

Models details expose things like relationships, connector metadata, user defined fields, and other advanced functionality.

![Model Details](/images/model_details.png)

Because Models are really nothing more than JavaScript functions, a code editor is also provided in Model Details to script anything that doesn't have a GUI representation including custom logic.

![Model Code Editor](/images/model_code_editor.png)

Express Serverless Platform provides a GUI experience to help you get started and gives you have complete control once you become a more advanced user. For more information on advanced features and customizing Models programatically through code refer to the [LoopBack model documentation](https://loopback.io/doc/en/lb3/Defining-models.html).

## Auto REST Generation
Once a Model is connected to a Connector it will automatically generate a REST interface and corresponding [Swagger/OpenAPIv2 specification](https://github.com/OAI/OpenAPI-Specification) and with fully functional endpoints.

{{% notice tip %}}
The REST Generation is not only automatic by dynamically updated as you edit your Model.
{{% /notice %}}

Click on the gear icon in the right hand toolbar to actiave the Settings Panel.
![LBWS urls](/images/settings_lbws_url.png)

Visit the URL listed for the API Explorer to try out the REST API.
![LBWS urls](/images/swagger_lbws.png)
