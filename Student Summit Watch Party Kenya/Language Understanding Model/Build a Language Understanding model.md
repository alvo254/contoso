# Introduction

Completed100 XP

-   2 minutes

_Natural language processing_ (NLP) is a common AI problem in which software must be able to work with text or speech in the natural language form that a human user would write or speak. Within the broader area of NLP, _natural language understanding_ (NLU) deals with the problem of determining semantic meaning from natural language - usually by using a trained language model.

A common design pattern for a language understanding solution looks like this image:

![Diagram showing an app accepts natural language input, and uses a model to determine semantic meaning before taking the appropriate action.](https://learn.microsoft.com/en-us/training/wwl-data-ai/build-language-understanding-model/media/language-understanding-app.png)

In this design pattern:

1.  An app accepts natural language input from a user
2.  A language model is used to determine semantic meaning (the user's _intent_)
3.  The app performs an appropriate action

In Microsoft Azure, the **Language Understanding** service enables developers to build apps based on language models that can be trained with a relatively small number of samples to discern a user's intended meaning.

In this module, you'll learn how to use the Language Understanding service to create a language understanding app.

After completing this module, you’ll be able to:

-   Provision Azure resources for the Language Understanding service
-   Define intents, entities, and utterances
-   Use patterns to differentiate similar utterances
-   Use pre-built entity components
-   Train, test, publish, and review a model


# Understand resources for building a language understanding model

Completed100 XP

-   9 minutes

To use the Language Understanding service to develop an NLP solution, you'll need to create a Language resource in Azure. That resource will be used for both authoring your model and processing prediction requests from client applications.

The Language service has various features, including sentiment analysis, key phrase extraction, entity recognition, intent recognition, and text classification. Some of these features can be used without configuration of your Language resource, such as language detection or sentiment analysis. Other features, such as conversational language understanding and custom named entity recognition will require a model to be built for prediction.

 Tip

This module's lab covers building a model for conversational language understanding. For more focused modules on custom text classification and custom named entity recognition, see the [Build custom text analytics](https://learn.microsoft.com/en-us/training/paths/build-custom-text-analytics) learning path.

## Building your Language Understanding model

For Language features that require a model for prediction, you'll need to build, train and deploy that model before using it to make a prediction. This building and training will teach the Language service what to look for.

First, you'll need to create your Language resource in the [Azure portal](https://portal.azure.com/).

1.  Click on **Create a new resource**
2.  Find and select **Language service**
3.  Click Create
4.  Fill out the necessary details, choosing the region closest to you geographically (for best performance) and giving it a unique name

Once that resource has been created, you'll need a key and the endpoint. You can find that on the left side under **Keys and Endpoint** of the resource overview page.

### Using the REST API

One way to build your model is through the REST API. The pattern would be to create your project, import data, train, deploy, then use your model.

These tasks are done asynchronously; you'll need to submit a request to the appropriate URI for each step, and then send another request to get the status of that job.

For example, if you want to deploy a model for a conversational language understanding project, you'd submit the deployment job, and then check on the deployment job status.

#### Authentication

For each call to your Language resource, you authenticate the request by providing the following header.

Key

Value

`Ocp-Apim-Subscription-Key`

The key to your resource

#### Request deployment

Submit a **POST** request to the following endpoint.

HTTPCopy

```
{ENDPOINT}/language/authoring/analyze-conversations/projects/{PROJECT-NAME}/deployments/{DEPLOYMENT-NAME}?api-version={API-VERSION}
```

Placeholder

Value

Example

`{ENDPOINT}`

The endpoint of your Language resource

`https://<your-subdomain>.cognitiveservices.azure.com`

`{PROJECT-NAME}`

The name for your project. This value is case-sensitive

`myProject`

`{DEPLOYMENT-NAME}`

The name for your deployment. This value is case-sensitive

`staging`

`{API-VERSION}`

The version of the API you're calling

`2022-05-01`

Include the following `body` with your request.

JSONCopy

```
{
  "trainedModelLabel": "{MODEL-NAME}",
}
```

Placeholder

Value

`{MODEL-NAME}`

The model name that will be assigned to your deployment. This value is case-sensitive.

Successfully submitting your request will receive a `202` response, with a response header of `location`. This header will have a URL with which to request the status, formatted like this:

HTTPCopy

```
{ENDPOINT}/language/authoring/analyze-conversations/projects/{PROJECT-NAME}/deployments/{DEPLOYMENT-NAME}/jobs/{JOB-ID}?api-version={API-VERSION}
```

#### Get deployment status

Submit a **GET** request to the URL from the response header above. The values will already be filled out based on the initial deployment request.

HTTPCopy

```
{ENDPOINT}/language/authoring/analyze-conversations/projects/{PROJECT-NAME}/deployments/{DEPLOYMENT-NAME}/jobs/{JOB-ID}?api-version={API-VERSION}
```

Placeholder

Value

`{ENDPOINT}`

The endpoint for authenticating your API request

`{PROJECT-NAME}`

The name for your project (case-sensitive)

`{DEPLOYMENT-NAME}`

The name for your deployment (case-sensitive)

`{JOB-ID}`

The ID for locating your model's training status, found in the header value detailed above in the deployment request

`{API-VERSION}`

The version of the API you're calling

The response body will give the deployment status details. The `status` field will have the value of _succeeded_ when the deployment is complete.

JSONCopy

```
{
    "jobId":"{JOB-ID}",
    "createdDateTime":"String",
    "lastUpdatedDateTime":"String",
    "expirationDateTime":"String",
    "status":"running"
}
```

For a full walkthrough of each step with example requests, see the [conversational understanding quickstart](https://learn.microsoft.com/en-us/azure/cognitive-services/language-service/conversational-language-understanding/quickstart?pivots=rest-api#create-a-clu-project).

### Using Language Studio

For a more visual method of building, training, and deploying your model, you can use [Language Studio](https://aka.ms/languageStudio) to achieve each of these steps. On the main page, you can select which type of project you want to create. Once the project is created, then go through the same process as above to build, train, and deploy your model.

[![Screenshot of Language Studio home page.](https://learn.microsoft.com/en-us/training/wwl-data-ai/build-language-understanding-model/media/language-studio-conversational.png)](https://learn.microsoft.com/en-us/training/wwl-data-ai/build-language-understanding-model/media/language-studio-conversational.png#lightbox)

The lab in this module will walk through using Language Studio to build your model. If you'd like to learn more, see the [Language Studio quickstart](https://learn.microsoft.com/en-us/azure/cognitive-services/language-service/language-studio)

## Querying your Language Understanding model

To query your model for a prediction, create a **POST** request to the appropriate URL with the appropriate body specified. For built in features such as language detection or sentiment analysis, you'll query the `analyze-text` endpoint.

 Tip

Remember each request needs to be authenticated with your Language resource key in the `Ocp-Apim-Subscription-Key` header

HTTPCopy

```
{ENDPOINT}/language/:analyze-text?api-version={API-VERSION}
```

Placeholder

Value

`{ENDPOINT}`

The endpoint for authenticating your API request

`{API-VERSION}`

The version of the API you're calling

Within the body of that request, you must specify the `kind` parameter, which tells the service what type of language understanding you're requesting.

If I want to detect the language, for example, my JSON body would look something like the following.

JSONCopy

```
{
    "kind": "LanguageDetection",
    "parameters": {
        "modelVersion": "latest"
    },
    "analysisInput":{
        "documents":[
            {
                "id":"1",
                "text": "This is a document written in English."
            }
        ]
    }
}
```

A sample response to your query would be similar to the following.

JSONCopy

```
{
    "kind": "LanguageDetectionResults",
    "results": {
        "documents": [{
            "id": "1",
            "detectedLanguage": {
                "name": "English",
                "iso6391Name": "en",
                "confidenceScore": 1.0
            },
            "warnings": []
        }],
        "errors": [],
        "modelVersion": "String"
    }
}
```

Other language features, such as the conversational language understanding discussed above, require the request be routed to a different endpoint. For example, the conversational language understanding request would be sent to the following.

HTTPCopy

```
{ENDPOINT}/language/:analyze-conversations?api-version={API-VERSION}
```

Placeholder

Value

`{ENDPOINT}`

The endpoint for authenticating your API request

`{API-VERSION}`

The version of the API you're calling

That request would include a JSON body similar to the following.

JSONCopy

```
{
  "kind": "Conversation",
  "analysisInput": {
    "conversationItem": {
      "id": "1",
      "participantId": "1",
      "text": "Sample text"
    }
  },
  "parameters": {
    "projectName": "{PROJECT-NAME}",
    "deploymentName": "{DEPLOYMENT-NAME}",
    "stringIndexType": "TextElement_V8"
  }
}
```

Placeholder

Value

`{PROJECT-NAME}`

The name of the project where you built your model

`{DEPLOYMENT-NAME}`

The name of your deployment

A sample response to your query would be similar to the following.

JSONCopy

```
{
  "kind": "ConversationResult",
  "result": {
    "query": "String",
    "prediction": {
      "topIntent": "intent1",
      "projectKind": "Conversation",
      "intents": [
        {
          "category": "intent1",
          "confidenceScore": 1
        },
        {
          "category": "intent2",
          "confidenceScore": 0
        }
      ],
      "entities": [
        {
          "category": "entity1",
          "text": "text",
          "offset": 7,
          "length": 4,
          "confidenceScore": 1
        }
      ]
    }
  }
}
```

For full documentation on features, including examples and how-to guides, see the [Azure Cognitive Service for Language](https://learn.microsoft.com/en-us/azure/cognitive-services/language-service/) documentation pages.

# Define intents, utterances, and entities

Completed100 XP

-   5 minutes

_Utterances_ are the phrases that a user might enter when interacting with an application that uses your Language Understanding model. An _intent_ represents a task or action the user wants to perform, or more simply the _meaning_ of an utterance. You create a model by defining intents and associating them with one or more utterances.

For example, consider the following list of intents and associated utterances:

-   **GetTime**:
    -   "What time is it?"
    -   "What is the time?"
    -   "Tell me the time"
-   **GetWeather**:
    -   "What is the weather forecast?"
    -   "Do I need an umbrella?"
    -   "Will it snow?"
-   **TurnOnDevice**
    -   "Turn the light on."
    -   "Switch on the light."
    -   "Turn on the fan"
-   **None**:
    -   "Hello"
    -   "Goodbye"

In a Language Understanding model, you must define the intents that you want your model to understand, so spend some time considering the _domain_ your model must support and the kinds of actions or information that users might request. In addition to the intents that you define, every model includes a **None** intent that you should use to explicitly identify utterances that a user might submit, but for which there is no specific action required (for example, conversational greetings like "hello") or that fall outside of the scope of the domain for this model.

After you've identified the intents your model must support, it's important to capture various different example utterances for each intent. Collect utterances that you think users will enter; including utterances meaning the same thing but that are constructed in different ways. Keep these guidelines in mind:

-   Capture multiple different examples, or alternative ways of saying the same thing
-   Vary the length of the utterances from short, to medium, to long
-   Vary the location of the _noun_ or _subject_ of the utterance. Place it at the beginning, the end, or somewhere in between
-   Use correct grammar and incorrect grammar in different utterances to offer good training data examples
-   The precision, consistency and completeness of your labeled data are key factors to determining model performance.
    -   Label **precisely**: Label each entity to its right type always. Only include what you want extracted, avoid unnecessary data in your labels.
    -   Label **consistently**: The same entity should have the same label across all the utterances.
    -   Label **completely**: Label all the instances of the entity in all your utterances.

_Entities_ are used to add specific context to intents. For example, you might define a **TurnOnDevice** intent that can be applied to multiple devices, and use entities to define the different devices.

Consider the following utterances, intents, and entities:

Utterance

Intent

Entities

What is the time?

GetTime

What time is it in _London_?

GetTime

Location (London)

What's the weather forecast for _Paris_?

GetWeather

Location (Paris)

Will I need an umbrella _tonight_?

GetWeather

Time (tonight)

What's the forecast for _Seattle tomorrow_?

GetWeather

Location (Seattle), Time (tomorrow)

Turn the _light_ on.

TurnOnDevice

Device (light)

Switch on the _fan_.

TurnOnDevice

Device (fan)

You can split entities into a few different component types:

-   **Learned** entities are the most flexible kind of entity, and should be used in most cases. You define a learned component with a suitable name, and then associate words or phrases with it in training utterances. When you train your model, it learns to match the appropriate elements in the utterances with the entity.
-   **List** entities are useful when you need an entity with a specific set of possible values - for example, days of the week. You can include synonyms in a list entity definition, so you could define a **DayOfWeek** entity that includes the values "Sunday", "Monday", "Tuesday", and so on; each with synonyms like "Sun", "Mon", "Tue", and so on.
-   **Prebuilt** entities are useful for common types such as numbers, datetimes, and names. For example, when prebuilt components are added, you will automatically detect values such as "6" or organizations such as "Microsoft". You can see this article for a list of [supported prebuilt entities](https://learn.microsoft.com/en-us/azure/cognitive-services/language-service/conversational-language-understanding/prebuilt-component-reference).


# Use patterns to differentiate similar utterances

Completed100 XP

-   2 minutes

In some cases, a model might contain multiple intents for which utterances are likely to be similar. You can use the pattern of utterances to disambiguate the intents while minimizing the number of sample utterances.

For example, consider the following utterances:

-   "Turn on the kitchen light"
-   "Is the kitchen light on?"
-   "Turn off the kitchen light"

These utterances are syntactically similar, with only a few differences in words or punctuation. However, they represent three different intents (which could be named **TurnOnDevice**, **GetDeviceStatus**, and **TurnOffDevice**). Additionally, the intents could apply to a wide range of entity values. In addition to "kitchen light", the intent could apply to "living room light", "bedside lamp", "fan", television", or any other device that the model might need to support.

To correctly train your model, provide a handful of examples of each intent that specify the different formats of utterances.

-   **TurnOnDevice**:
    -   "Turn the {DeviceName} on"
    -   "Switch the {DeviceName} on"
    -   "Turn on the {DeviceName}"
-   **GetDeviceStatus**:
    -   "Is the {DeviceName} on[?]"
-   **TurnOffDevice**:
    -   "Turn the {DeviceName} off"
    -   "Switch the {DeviceName} off"
    -   "Turn off the {DeviceName}"

When you teach your model with each different type of utterance, the Language service can learn how to categorize intents correctly based off format and punctuation.


# Use pre-built entity components

Completed100 XP

-   1 minute

You can create your own language models by defining all the intents and utterances it requires, but often you can use prebuilt components to detect common entities such as numbers, emails, URLs, or choices.

For a full list of prebuilt entities the Language service can detect, see the list of [supported prebuilt entity components.](https://learn.microsoft.com/en-us/azure/cognitive-services/language-service/conversational-language-understanding/prebuilt-component-reference).

Using prebuilt components allows you to let the Language service automatically detect the specified type of entity, and not have to train your model with examples of that entity.

To add a prebuilt component, you can create an entity in your project, then click "Add new prebuilt" to that entity to detect certain entities.

[![Screenshot of adding a prebuilt entity component.](https://learn.microsoft.com/en-us/training/wwl-data-ai/build-language-understanding-model/media/add-prebuilt-entity.png)](https://learn.microsoft.com/en-us/training/wwl-data-ai/build-language-understanding-model/media/add-prebuilt-entity.png#lightbox)

You can have up to five prebuilt components per entity. Using prebuilt model elements can significantly reduce the time it takes to develop a language understanding solution.

# Train, test, publish, and review a Language Understanding model

Completed100 XP

-   1 minute

Creating a language understanding model is an iterative process with the following activities:

![Diagram that shows the train, test, publish, review cycle.](https://learn.microsoft.com/en-us/training/wwl-data-ai/build-language-understanding-model/media/train-test-publish-review.png)

1.  Train a model to learn intents and entities from sample utterances.
2.  Test the model interactively or using a testing dataset with known labels
3.  Deploy a trained model to a public endpoint so client apps can use it
4.  Review predictions and iterate on utterances to train your model

By following this iterative approach, you can improve the language model over time based on user input, helping you develop solutions that reflect the way users indicate their intents using natural language.

# Exercise - Build a Language Understanding model

Completed100 XP

-   35 minutes

This unit includes a lab to complete.

Use the free resources provided in the lab to complete the exercises in this unit. You will not be charged.

Microsoft provides this lab experience and related content for educational purposes. All presented information is owned by Microsoft and intended solely for learning about the covered products and services in this Microsoft Learn module.

Launch lab

 Note

To complete this exercise, you will need a Microsoft Azure subscription. If you don't already have one, you can sign up for a free trial at [https://azure.com/free](https://azure.com/free).

A virtual machine (VM) containing the client tools you need is provided, along with the exercise instructions. Use the button above to open the VM. A limited number of concurrent sessions are available - if the hosted environment is unavailable, try again later.

Alternatively, if you would like to use a development environment on your own computer, you can use this [setup guide](https://microsoftlearning.github.io/AI-102-AIEngineer/Instructions/00-setup.html) and follow these [exercise instructions](https://microsoftlearning.github.io/AI-102-AIEngineer/Instructions/09b-language-understanding-(preview).html). Note that the setup guide is designed for multiple AI development exercises, and may include software that is not required for this specific exercise. Additionally, due to the range of possible operating systems and setup configurations, we can't provide support if you choose to complete the exercise on your own computer.

When you finish the exercise, end the lab to close the VM. Don't forget to come back and complete the knowledge check to earn points for completing this module!

 Tip

After completing the exercise, if you've finished exploring Azure cognitive services, delete the Azure resources that you created during the exercise.