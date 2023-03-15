**Azure Cognitive Services** are cloud-based services that encapsulate AI capabilities. Rather than a single product, you should think of Azure Cognitive Services as a set of individual services that you can use as building blocks to compose sophisticated, intelligent applications.

Cognitive services includes a wide range of individual AI services across multiple categories, as shown in the following table.

Language

Speech

Vision

Decision

Language

Speech

Computer Vision

Anomaly Detector

Translator

Custom Vision

Content Moderator

Face

Personalizer

You can use Cognitive Services to build your own AI solutions, and they also underpin _Azure Applied AI Services_ that provide out-of-the-box solutions for common AI scenarios. Applied AI Services include:

-   **Azure Form Recognizer** - an optical character recognition (OCR) solution that can extract semantic meaning from forms, such as invoices, receipts, and others.
-   **Azure Metrics Advisor** - A service built on the Anomaly Detector cognitive service that simplifies real-time monitoring and response to critical metrics.
-   **Azure Video Analyzer for Media** - A comprehensive video analysts solution build on the Video Indexer cognitive service.
-   **Azure Immersive Reader** - A reading solution that supports people of all ages and abilities.
-   **Azure Bot Service** - A cloud service for delivering conversational AI solutions, or _bots_.
-   **Azure Cognitive Search** - A cloud-scale search solution that uses cognitive services to extract insights from data and documents.

While the details of each cognitive service can vary, the approach to provisioning and consuming them is generally the same.

In this module, you will learn how to:

-   Provision cognitive service resources in an Azure subscription.
-   Identify endpoints, keys, and locations required to consume a cognitive service resource.
-   Use a REST API to consume a cognitive service.
-   Use an SDK to consume a cognitive service.


# Provision a cognitive services resource

Completed100 XP

-   3 minutes

Azure Cognitive Services include a wide range of AI capabilities that you can use in your applications. To use any of the cognitive services, you need to create appropriate resources in an Azure subscription to define an endpoint where the service can be consumed, provide access keys for authenticated access, and to manage billing for your application's usage of the service.

## Options for Azure resources

For many of the available cognitive services, you can choose between the following provisioning options:

### Multi-service resource

You can provision a **Cognitive Services** resource that supports multiple different cognitive services. For example, you could create a single resource that enables you to use the **Language**, **Computer Vision**, **Speech**, and other services.

This approach enables you to manage a single set of access credentials to consume multiple services at a single endpoint, and with a single point of billing for usage of all services.

### Single-service resource

Each cognitive service can be provisioned individually, for example by creating discrete **Language** and **Computer Vision** resources in your Azure subscription.

This approach enables you to use separate endpoints for each service (for example to provision them in different geographical regions) and to manage access credentials for each service independently. It also enables you to manage billing separately for each service.

Single-service resources generally offer a free tier (with usage restrictions), making them a good choice to try out a service before using it in a production application.

## Training and prediction resources

While most cognitive services can be used through a single Azure resource, some offer (or require) separate resources for model _training_ and _prediction_. This enables you to manage billing for training custom models separately from model consumption by applications, and in most cases enables you to use a dedicated service-specific resource to train a model, but a generic **Cognitive Services** resource to make the model available to applications for inferencing.


# Identify endpoints and keys

Completed100 XP

-   2 minutes

When you provision a cognitive service resource in your Azure subscription, you are defining an endpoint through which the service can be consumed by an application.

To consume the service through the endpoint, applications require the following information:

-   **The endpoint URI**. This is the HTTP address at which the REST interface for the service can be accessed. Most cognitive services software development kits (SDKs) use the endpoint URI to initiate a connection to the endpoint.
-   **A subscription key**. Access to the endpoint is restricted based on a subscription key. Client applications must provide a valid key to consume the service. When you provision a cognitive services resource, two keys are created - applications can use either key. You can also regenerate the keys as required to control access to your resource.
-   **The resource location**. When you provision a resource in Azure, you generally assign it to a location, which determines the Azure data center in which the resource is defined. While most SDKs use the endpoint URI to connect to the service, some require the location.


# Use a REST API

Completed100 XP

-   3 minutes

Cognitive services provide REST application programming interfaces (APIs) that client applications can use to consume services. In most cases, service functions can be called by submitting data in JSON format over an HTTP request, which may be a POST, PUT, or GET request depending on the specific function being called. The results of the function are returned to the client as an HTTP response, often with JSON contents that encapsulate the output data from the function.

![An app submits a JSON request to a cognitive services REST API and receives a JSON response](https://learn.microsoft.com/en-us/training/wwl-data-ai/create-manage-cognitive-services/media/rest-api.png)

The use of REST interfaces with an HTTP endpoint means that any programming language or tool capable of submitting and receiving JSON over HTTP can be used to consume cognitive services. You can use common programming languages such as Microsoft C#, Python, and JavaScript; as well as utilities such as Postman and cURL, which can be useful for testing.


# Use an SDK

Completed100 XP

-   3 minutes

You can develop an application that uses cognitive services using REST interfaces, but it is easier to build more complex solutions by using native libraries for the programming language in which you are developing the application.

![An app submits a call to a cognitive services resource through a language-specific SDK, which abstracts the JSON request and response](https://learn.microsoft.com/en-us/training/wwl-data-ai/create-manage-cognitive-services/media/sdk.png)

Software development kits (SDKs) for common programming languages abstract the REST interfaces for most cognitive services. SDK availability varies by individual cognitive services, but for most services there is an SDK for languages such as:

-   Microsoft C# (.NET Core)
-   Python
-   JavaScript (Node.js)
-   Go
-   Java

Each SDK includes packages that you can install in order to use service-specific libraries in your code, and online documentation to help you determine the appropriate classes, methods, and parameters used to work with the service.


# Exercise - Use cognitive services

Completed100 XP

-   30 minutes

This unit includes a lab to complete.

Use the free resources provided in the lab to complete the exercises in this unit. You will not be charged.

Microsoft provides this lab experience and related content for educational purposes. All presented information is owned by Microsoft and intended solely for learning about the covered products and services in this Microsoft Learn module.

Launch lab

 Note

To complete this exercise, you will need a Microsoft Azure subscription. If you don't already have one, you can sign up for a free trial at [https://azure.com/free](https://azure.com/free).

A virtual machine (VM) containing the client tools you need is provided, along with the exercise instructions. Use the button above to open the VM. A limited number of concurrent sessions are available - if the hosted environment is unavailable, try again later.

Alternatively, if you would like to use a development environment on your own computer, you can use this [setup guide](https://microsoftlearning.github.io/AI-102-AIEngineer/Instructions/00-setup.html) and follow these [exercise instructions](https://microsoftlearning.github.io/AI-102-AIEngineer/Instructions/01-get-started-cognitive-services.html). Note that the setup guide is designed for multiple AI development exercises, and may include software that is not required for this specific exercise. Additionally, due to the range of possible operating systems and setup configurations, we can't provide support if you choose to complete the exercise on your own computer.

When you finish the exercise, end the lab to close the VM. Don't forget to come back and complete the knowledge check to earn points for completing this module!

 Tip

After completing the exercise, if you've finished exploring Azure cognitive services, delete the Azure resources that you created during the exercise.