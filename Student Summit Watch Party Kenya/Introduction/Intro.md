
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

## Next unit: Exercise - Create a timer trigger