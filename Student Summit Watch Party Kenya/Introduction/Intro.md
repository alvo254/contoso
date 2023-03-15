
Imagine a scenario where a busy hair salon has a recurring problem: customers commonly miss their appointments. Appointments are reserved time slots, so if a customer misses an appointment, the salon loses money. To fix this problem, the salon reaches out to you, a software developer. To improve the situation, you decide to send two types of reminder text messages, one that is sent as soon as the appointment is scheduled or changed, and each morning send a text message to each customer who has an appointment that day.

You need to create a service that can be easily scheduled, updated, and scaled. You decide to solve this problem using an Azure Functions app. You already know how to implement the logic to send a text message. Now you need to learn how to send the message at a specific time or when a specific event occurs. Luckily, Azure Functions app supports a feature called _triggers_. Triggers are used to determine how an Azure Function is invoked.

## Learning objectives

In this module, you will:

-   Determine which trigger works best for your business needs.
-   Create a timer trigger to invoke a function on a consistent schedule.
-   Create an HTTP trigger to invoke a function when an HTTP request is received.
-   Create a blob trigger to invoke a function when a blob is created or updated in Azure Storage.

## Supported languages

This module uses the Azure portal to create and test your function code. Functions supports in-portal development for the following languages:

-   C# Script (.csx)
-   JavaScript
-   Python
-   PowerShell

Other languages such as Java, TypeScript, Go and Rust are supported by Azure Functions through local development tools. You can read more about the supported languages, tools, and features of Azure Functions in the [developer guide](https://learn.microsoft.com/en-us/azure/azure-functions/functions-reference).

---

# Determine the best trigger for your Azure function

An Azure Functions app doesn't do work until something tells it to execute. For example, we could create an Azure Function to send out a reminder text message to our customers before an appointment. If we don't tell the function when it should run, our customers will never receive a message.

This unit describes triggers at a high level, explores the most common types of triggers, and uses bindings to connect a trigger to a function.

## What is a trigger?

A trigger is an object that defines how an Azure Function is invoked. For example, if you want a function to execute every 10 minutes, you could use a timer trigger.

Every function must have exactly one trigger associated with it. If you want to execute a piece of logic that runs under multiple conditions, you need to create multiple functions that share the same core function code.

In this module, we're going to focus on three trigger types: **timer**, **HTTP**, and **blob**.

## Types of triggers

Azure Functions supports a wide range of trigger types. Here are some of the most common types:

Type

Purpose

**Timer**

Execute a function at a set interval.

**HTTP**

Execute a function when an HTTP request is received.

**Blob**

Execute a function when a file is uploaded or updated in Azure Blob storage.

**Queue**

Execute a function when a message is added to an Azure Storage queue.

**Azure Cosmos DB**

Execute a function when a document changes in a collection.

**Event Hub**

Execute a function when an event hub receives a new event.

## What is a binding?

A binding is a connection to data within your function. Bindings are optional and can be input bindings, output bindings, or both. An input binding is the data that your function receives. An output binding is the data that your function sends.

Unlike a trigger, a function can have multiple input bindings and output bindings.

In the next exercise, we'll run a function on a schedule using a Timer trigger.

---

# Run an Azure Function on a schedule

It's common to execute a piece of logic at a set interval. Imagine you're a blog owner and you notice that your subscribers aren't reading your most recent posts. You decide that the best action is to send an email once a week to remind them to check your blog. You implement this logic using an Azure function app with a _timer trigger_ to invoke your function weekly.

## What is a timer trigger?

A timer trigger is a trigger that executes a function at a consistent interval. To create a timer trigger, you need to supply two pieces of information.

1.  A _Timestamp parameter name_, which is simply an identifier to access the trigger in code.
2.  A _Schedule_, which is a CRON expression that sets the interval for the timer.

## What is a CRON expression?

A _CRON expression_ is a string that consists of six fields that represent a set of times.

The order of the six fields in Azure is: `{second} {minute} {hour} {day} {month} {day of the week}`.

For example, a CRON expression to create a trigger that executes every five minutes looks like: `0 */5 * * * *`

At first, this string may look confusing. We'll come back and break down these concepts when we have a deeper look at CRON expressions.

To build a CRON expression, you need to have a basic understanding of some of the special characters.

Special character

Meaning

Example

*

Selects every value in a field

An asterisk "*" in the day of the week field means _every_ day.

,

Separates items in a list

A comma "1,3" in the day of the week field means just Mondays (day 1) and Wednesdays (day 3).

-

Specifies a range

A hyphen "10-12" in the hour field means a range that includes the hours 10, 11, and 12.

/

Specifies an increment

A slash "*/10" in the minutes field means an increment of every 10 minutes.

Now we'll go back to the original CRON expression example. Let’s try to understand it better by breaking it down field by field.

textCopy

```
0 */5 * * * *
```

The **first field** represents seconds. This field supports the values 0-59. Because the field contains a zero, it selects the first possible value, which is one second.

The **second field** represents minutes. The value "*/5" contains two special characters. First, the asterisk (*) means "select every value within the field." Because this field represents minutes, the possible values are 0-59. The second special character is the slash (/), which represents an increment. When you combine these characters together, it means for all values 0-59, select every fifth value. An easier way to say that is simply "every five minutes."

The **remaining four fields** represent the hour, day, month, and weekday of the week. An asterisk for these fields means to select every possible value. In this example, we select "every hour of every day of every month."

When you put all the fields together, the expression is read as "the first second of every fifth minute of every hour, of every day, of every month".

## How to create a timer trigger

You can create a timer trigger in the Azure portal. In your Azure function app, select **timer trigger** from the list of trigger templates. Enter the logic that you want to execute. Supply a **Timestamp parameter name** and the **CRON expression**.

In this module, we'll focus on creating triggers in the portal but you can also create triggers programmatically using Core Tools, Visual Studio or Visual Studio Code.

A timer trigger invokes an Azure function app on a consistent schedule. To define the schedule for a timer trigger, we build a CRON expression, which is a string that represents a set of times.

---

# Exercise - Create a timer trigger


You have used 1 of 10 sandboxes for today. More sandboxes will be available tomorrow.

In this unit, we create an Azure Function app that's invoked every 20 seconds using a timer trigger.

## Create an Azure Function App

Let’s start by creating an Azure Function App in the portal.

1.  Sign in to the [Azure portal](https://portal.azure.com/learn.docs.microsoft.com) using the same account you used to activate the sandbox.
    
2.  Under **Azure services**, select **Create a resource**.
    
    ![Screenshot of Azure portal menu and Create a resource option.](https://learn.microsoft.com/en-us/training/modules/execute-azure-function-with-triggers/media/4-create-a-resource.png)
    
    The **Create a resource** pane appears.
    
3.  In the **Create a resource** menu, select **Web**, and then select **Function App** from the results. Optionally, you can enter **Function App** in the search bar, and press Enter. On the **Function App** pane that appears, select **Create**. The **Create Function App** pane appears.
    
4.  On the **Basics** tab, enter the following values for each setting.
    
    Setting
    
    Value
    
    **Project Details**
    
    Subscription
    
    Select the **Concierge Subscription** for this exercise
    
    Resource Group
    
    Select 'learn-5ed9f517-1921-42b5-9506-9e5e7a5993c1' resource group from the dropdown list.
    
    **Instance Details**
    
    Function App name
    
    _<your-webapp-name>_. Enter a globally unique name for your function app.
    
    Publish
    
    Code
    
    Runtime stack
    
    Select one of the languages supported for in-portal development: **.NET**, **Node.js**, or **PowerShell Core**.
    
    Version
    
    Use the suggested default version of your language runtime.
    
    Region
    
    Select a location close to you.
    
    **Operating system**
    
    Operating System
    
    Windows
    
    **Plan**
    
    Plan type
    
    Consumption (Serverless). When using the Consumption Plan type, you're charged for each execution of your function, and resources are automatically allocated based on your app workload.
    
5.  Select **Next : Hosting**, and enter the following values for each setting.
    
    Setting
    
    Value
    
    **Storage**
    
    Storage account
    
    Defaults to (New) and a unique storage account name. You can change the name if you like.
    
6.  Select **Review + create** to validate your input, and then select **Create**. Deployment progress displays the items that are created. It may take a minute or two for deployment to complete.
    
7.  When deployment is complete, select **Go to resource**. The **Overview** pane for your _Function App_ appears.
    

## Create and configure a timer-triggered function

Let's create a timer trigger in your function.

1.  In the **Function App** menu, under **Functions**, select **Functions**. The **Functions** pane for your _Function App_ appears.
    
2.  On the command bar, select **Create**. It may take a few moments for your permissions to propagate to use this service. The **Create function** pane appears.
    
3.  Under **Select a template**, select **Timer trigger**.
    
4.  Under **Template details**, enter the following value into the **Schedule** field, and then select **Create**.
    
    logCopy
    
    ```
    */20 * * * * *
    ```
    
    The value in this parameter represents the CRON expression with six places for time precision: {second} {minute} {hour} {day} {month} {day-of-week}. The first place value represents every 20 seconds.
    

## Test the timer

Now that we've configured the timer, it will invoke the function on the interval we defined.

1.  On the **TimerTrigger1** pane, in the left menu pane, under **Developer**, select **Code + Test**. The **Code + Test** pane appears.
    
     Note
    
    Azure automatically provides a default name for a new trigger that you create. **TimerTrigger1** is default value that you can change when you create a new trigger.
    
2.  The **Logs** session pane opens at the bottom of the page. Select the **App Insight Logs** drop-down, and then select **Filesystem Logs**. Select **OK** when the **Switching to filesystem based logs...** message displays.
    
    ![Screenshot that shows the function Code + Test pane with the Filesystem Log displayed.](https://learn.microsoft.com/en-us/training/modules/execute-azure-function-with-triggers/media/4-azure-function-logs.png)
    
3.  Observe that a new message arrives every 20 seconds in the log pane.
    
4.  To stop the function, select **Stop** in the command bar of the _Logs_ pane.
    
5.  To disable the function, in the **TimerTrigger1** menu, select **Overview**, and then in the command bar, select **Disable**.
    

---


# Execute an Azure function with an HTTP request


An HTTP request is a common operation on most platforms and devices. Whether it's a request to look up a word in a dictionary or to get the local weather, we send HTTP requests all the time. Azure Functions allows us to quickly create a piece of logic to execute when an HTTP request is received.

In this unit, you'll learn how to create and invoke an Azure function using an HTTP trigger. You'll also explore some of the customization options available for HTTP triggers.

## What is an HTTP trigger?

An HTTP trigger is a trigger that executes a function when it receives an HTTP request. HTTP triggers have many capabilities and customizations, including:

-   Provide authorized access by supplying keys.
-   Restrict which HTTP verbs are supported.
-   Return data back to the caller.
-   Receive data through query string parameters or through the request body.
-   Support URL route templates to modify the function URL.

When you create an HTTP trigger, you need to select a programming language, provide a trigger name, and select an Authorization level.

## What is an HTTP trigger Authorization level?

An HTTP trigger Authorization level is a flag that indicates whether an incoming HTTP request needs an API key for authentication.

There are three Authorization levels:

1.  Function
2.  Anonymous
3.  Admin

The **Function** and **Admin** levels are "key" based. To send an HTTP request, you must supply a key for authentication. There are two types of keys: _function_ and _host_. The difference between the two keys is their scope. Function keys are specific to a function. Host keys apply to all functions inside the function app. If your Authorization level is set to **Function**, you can use either a _function_ or a _host_ key. If your Authorization level is set to **Admin**, you must supply a _host_ key.

The **Anonymous** level means that authentication isn't required. This exercise uses the Anonymous authorization level.

## How to create an HTTP trigger

Just like a timer trigger, you can create an HTTP trigger through the Azure portal. Inside your Azure function, select **HTTP trigger** from the list of predefined trigger types, then enter the logic that you want to execute and make any customizations, like restricting the use of certain HTTP verbs.

One setting that's important to understand is **Request parameter name**. This setting is a string that represents the name of the parameter that contains the information about an incoming HTTP request. By default, the name of the parameter is _req_.

## How to invoke an HTTP trigger

To invoke an HTTP trigger, you send an HTTP request to the URL for your function. To get this URL, go to the code page for your function and select the **Get function URL** link.

![Screenshot of the Azure portal showing a Functions App pane with the app's Get function URL button highlighted.](https://learn.microsoft.com/en-us/training/modules/execute-azure-function-with-triggers/media/5-function-url.png)

After you have the URL for your function, you can send HTTP requests. If your function receives data, remember that you can either use query string parameters or supply the data through the request body.

An HTTP trigger invokes an Azure function when it receives an HTTP request to its function URL. HTTP triggers allow you to receive data and return data back to the caller.


# Exercise - Create an HTTP trigger


You have used 1 of 10 sandboxes for today. More sandboxes will be available tomorrow.

In this unit, we're going to create an Azure function that accepts an HTTP request with a single string. The function returns a string back to the caller to represent success or failure. We'll continue working on the function from the previous exercise.

## Create an HTTP trigger

Let's continue using our existing Azure Functions app and add an HTTP trigger.

1.  Make sure you're signed into the [Azure portal](https://portal.azure.com/learn.docs.microsoft.com) using the same account you activated the sandbox with.
    
2.  On the Azure portal menu or from the **Home** page, under **Azure services**, select **All resources**.
    
3.  Select your Function App identified under the _Type_ column. Your **Function App** pane appears.
    
4.  In the left menu pane, under **Functions**, select **Functions**. The **Functions** pane for your function app appears.
    
5.  On the top menu bar, select **Create**. This action starts the function creation process. The **Create function** pane appears.
    
6.  In the **Select a template** section, select **HTTP trigger**.
    
7.  In the **Template details** section, in **New Function** field, enter a name for the function. Scroll down and in the **Authorization level** dropdown list, select _Anonymous_, and then select **Create**. Your newly created Function pane appears.
    
8.  In the left menu pane, under **Developer**, select **Code + Test**, and review the auto-generated code to get an idea about what's going on. The _req_ parameter represents the incoming request and contains a _name_ parameter. Check to see if _name_ has a value. If it does, we return a greeting. Otherwise, it continues to ask for a value.
    

## Get your function URL

Now that we've created the HTTP trigger, let's get the function URL so we can begin to make a request.

1.  On the top menu bar, select **Get Function Url**. The **Get Function Url** dialog appears.
    
2.  In the **URL** field, select the **Copy to clipboard** icon.
    

## Issue a GET request to your HTTP trigger

Let's issue a GET request for the URL to see if we get a response.

1.  Open a new tab in your web browser.
    
2.  Paste the URL into the address bar.
    
3.  Add a query parameter called _name_ with your name to the URL; for example, `https://<your-webapp-name>.azurewebsites.net/api/HttpTrigger1?name=Jesse`
    
4.  Press Enter to submit the request.
    
5.  The message, **Hello, Jesse. This HTTP triggered function executed successfully.** displays.

# Execute an Azure function when a blob is created

Completed100 XP

-   10 minutes

Imagine you're a photographer and you have a website that displays your pictures of the day. Because you're busy, you don't have a consistent upload schedule, but you want to notify your fans when you upload a picture. You decide to create an Azure function to automatically send a tweet whenever you upload an image to your Azure Storage blob container.

Here, you learn how to create a blob trigger and instruct it to monitor a specific location in your Azure Storage blob container.

## What is Azure Storage?

Azure Storage is Microsoft's cloud storage solution that supports all types of data, including: blobs, queues, and NoSQL. The goal of Azure Storage is to provide data storage that's:

-   Highly available
-   Secure
-   Scalable
-   Managed

We're not going to focus on Azure Storage too much. Instead, we use it to create blobs that will trigger our function to run.

## What is Azure Blob storage?

Azure Blob storage is an object storage solution that's designed to store large amounts of unstructured data.

For example, Azure Blob storage is great at doing things like:

-   Storing files
-   Serving files
-   Streaming video and audio
-   Logging data

There are three types of blobs: **block blobs**, **append blobs**, and **page blobs**. Block blobs are the most common type. They allow you to store text or binary data efficiently. Append blobs are like block blobs, but they're designed more for append operations like creating a log file that's being constantly updated. Finally, page blobs are made up of pages and are designed for frequent random read and write operations.

## What is a blob trigger?

A blob trigger is a trigger that executes a function when a file is uploaded or updated in Azure Blob storage. To create a blob trigger, you create an Azure Storage account and provide a location that the trigger monitors.

## How to create a blob trigger

Just like the other triggers we've seen so far, you create a blob trigger in the Azure portal. Inside your Azure function, select **Blob trigger** from the list of predefined trigger types. Then, you enter the logic that you want to execute when a blob is created or updated.

One setting that's important to understand is the **Path**. The **Path** tells the blob trigger where to monitor to see if a blob is uploaded or updated. By default, the **Path** value is:

Copy

```
samples-workitems/{name}
```

Let's break down this concept into two pieces: _samples-workitems_ and _{name}_. The first part, _samples-workitems_, represents the blob container that the trigger monitors. The second part, _{name}_ means that every type of file will cause the trigger to invoke the function. The function is invoked because there's no filter. For example, we could make the trigger invoke the function only when a PNG file is added by using syntax like:

Copy

```
samples-workitems/{name}.png
```

The last significant piece of information for this concept is the text _name_. The _name_ represents a parameter in your Azure function that receives the name of the added file. For example, if we upload a file named _resume.txt_, my Azure function receives that value as a string through a parameter called _name_.

A blob trigger invokes an Azure function when it sees activity at a specific location in your Azure Storage blob account. You set the location to monitor by modifying the **Path** value in the Azure portal.