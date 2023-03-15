# Describe continuous integration with actions



It's an example of a basic continuous integration workflow created by using actions:

YAMLCopy

```
name: dotnet Build

on: [push]

jobs:
    build:
        runs-on: ubuntu-latest
        strategy:
            matrix:
                node-version: [10.x]
        steps:

        - uses: actions/checkout@main
        - uses: actions/setup-dotnet@v1
            with:
                dotnet-version: '3.1.x'

        - run: dotnet build awesomeproject

```

-   **On:** Specifies what will occur when code is pushed.
-   **Jobs:** There's a single job called **build.**
-   **Strategy:** It's being used to specify the Node.js version.
-   **Steps:** Are doing a checkout of the code and setting up dotnet.
-   **Run:** Is building the code.

# Examine environment variables


When using Actions to create CI or CD workflows, you'll typically need to pass variable values to the actions. It's done by using Environment Variables.

## Built-in environment variables

GitHub provides a series of built-in environment variables. It all has a GITHUB_ prefix.

 Note

Setting that prefix for your variables will result in an error.

Examples of built-in environment variables are:

**GITHUB_WORKFLOW** is the name of the workflow.

**GITHUB_ACTION** is the unique identifier for the action.

**GITHUB_REPOSITORY** is the name of the repository (but also includes the name of the owner in owner/repo format)

## Using variables in workflows

Variables are set in the YAML workflow files. They're passed to the actions that are in the step.

YAMLCopy

```
jobs:
    verify-connection:
        steps:
            - name: Verify Connection to SQL Server
            - run: node testconnection.js
        env:
            PROJECT_SERVER: PH202323V
            PROJECT_DATABASE: HAMaster

```

For more information on environment variables, including a list of built-in environment variables, see [Environment variables](https://docs.github.com/actions/learn-github-actions/environment-variables).

# Share artifacts between jobs

Completed100 XP

-   2 minutes

When using Actions to create CI or CD workflows, you'll often need to pass artifacts created by one job to another.

The most common ways to do it are by using the **upload-artifact** and **download-artifact** actions.

## Upload-artifact

This action can upload one or more files from your workflow to be shared between jobs.

You can upload a specific file:

YAMLCopy

```

- uses: actions/upload-artifact
  with:
    name: harness-build-log
    path: bin/output/logs/harness.log

```

You can upload an entire folder:

YAMLCopy

```

- uses: actions/upload-artifact
  with:
    name: harness-build-logs
    path: bin/output/logs/

```

You can use wildcards:

YAMLCopy

```

- uses: actions/upload-artifact
  with:
    name: harness-build-logs
    path: bin/output/logs/harness[ab]?/*

```

You can specify multiple paths:

YAMLCopy

```

- uses: actions/upload-artifact
  with:
    name: harness-build-logs
    path: |
        bin/output/logs/harness.log
        bin/output/logs/harnessbuild.txt

```

For more information on this action, see [upload-artifact.](https://github.com/actions/upload-artifact)

## Download-artifact

There's a corresponding action for downloading (or retrieving) artifacts.

YAMLCopy

```

- uses: actions/download-artifact
  with:
    name: harness-build-log

```

If no path is specified, it's downloaded to the current directory.

For more information on this action, see [download-artifact.](https://github.com/actions/download-artifact)

## Artifact retention

A default retention period can be set for the repository, organization, or enterprise.

You can set a custom retention period when uploading, but it can't exceed the defaults for the repository, organization, or enterprise.

YAMLCopy

```

- uses: actions/upload-artifact
  with:
    name: harness-build-log
    path: bin/output/logs/harness.log
    retention-days: 12

```

## Deleting artifacts

You can delete artifacts directly in the GitHub UI.

For details, you can see: [Removing workflow artifacts](https://docs.github.com/actions/managing-workflow-runs/removing-workflow-artifacts).

# Examine Workflow badges



Badges can be used to show the status of a workflow within a repository.

They show if a workflow is currently passing or failing. While they can appear in several locations, they typically get added to the README.md file for the repository.

Badges are added by using URLs. The URLs are formed as follows:



Where:

-   AAAAA is the account name.
-   RRRRR is the repository name.
-   WWWWW is the workflow name.

![Screenshot of the Badge failing in a color to represent an error.](https://learn.microsoft.com/en-us/training/wwl-azure/learn-continuous-integration-github-actions/media/badge-failing-12fd7192.png)

They usually indicate the status of the default branch but can be branch-specific. You do this by adding a URL query parameter:

?branch=BBBBB

where:

-   BBBBB is the branch name.

For more information, see: [Adding a workflow status badge](https://docs.github.com/actions/monitoring-and-troubleshooting-workflows/adding-a-workflow-status-badge).

# Describe best practices for creating actions



It's essential to follow best practices when creating actions:

-   Create chainable actions. Don't create large monolithic actions. Instead, create smaller functional actions that can be chained together.
-   Version your actions like other code. Others might take dependencies on various versions of your actions. Allow them to specify versions.
-   Provide the **latest** label. If others are happy to use the latest version of your action, make sure you provide the **latest** label that they can specify to get it.
-   Add appropriate documentation. As with other codes, documentation helps others use your actions and can help avoid surprises about how they function.
-   Add details **action.yml** metadata. At the root of your action, you'll have an **action.yml** file. Ensure it has been populated with author, icon, expected inputs, and outputs.
-   Consider contributing to the marketplace. It's easier for us to work with actions when we all contribute to the marketplace. Help to avoid people needing to relearn the same issues endlessly.


# Mark releases with Git tags


Releases are software iterations that can be packed for release.

In Git, releases are based on Git tags. These tags mark a point in the history of the repository. Tags are commonly assigned as releases are created.

![Screenshot of Git Release Tag creation page.](https://learn.microsoft.com/en-us/training/wwl-azure/learn-continuous-integration-github-actions/media/git-release-tag-28ff3ca4.png)

Often these tags will contain version numbers, but they can have other values.

Tags can then be viewed in the history of a repository.

![Screenshot of the Git release tag page showing the tag information.](https://learn.microsoft.com/en-us/training/wwl-azure/learn-continuous-integration-github-actions/media/tag-history-ed9cbbd4.png)

For more information on tags and releases, see: [About releases](https://docs.github.com/repositories/releasing-projects-on-github/about-releases).


# Create encrypted secrets


Actions often can use secrets within pipelines. Common examples are passwords or keys.

In GitHub actions, It's called **Secrets**.

## Secrets

Secrets are similar to environment variables but encrypted. They can be created at two levels:

-   Repository
-   Organization

If secrets are created at the organization level, access policies can limit the repositories that can use them.

## Creating secrets for a repository

To create secrets for a repository, you must be the repository's owner. From the repository **Settings**, choose **Secrets**, then **New Secret**.

![Screenshot of new secret creation from settings.](https://learn.microsoft.com/en-us/training/wwl-azure/learn-continuous-integration-github-actions/media/new-secret-5ba1255e.png)

For more information on creating secrets, see [Encrypted secrets](https://docs.github.com/actions/security-guides/encrypted-secrets).

# Use secrets in a workflow



Secrets aren't passed automatically to the runners when workflows are executed.

Instead, when you include an action that requires access to a secret, you use the **secrets** context to provide it.

YAMLCopy

```
steps:

  - name: Test Database Connectivity
    with:
      db_username: ${{ secrets.DBUserName }}
      db_password: ${{ secrets.DBPassword }}

```

## Command-line secrets

Secrets shouldn't be passed directly as command-line arguments as they may be visible to others. Instead, treat them like environment variables:

YAMLCopy

```
steps:

  - shell: pwsh
    env:
      DB_PASSWORD: ${{ secrets.DBPassword }}
    run: |
      db_test "$env:DB_PASSWORD"

```

## Limitations

Workflows can use up to 100 secrets, and they're limited to 64 KB in size.

For more information on creating secrets, see [Encrypted secrets](https://docs.github.com/actions/security-guides/encrypted-secrets).


# Implement GitHub Actions For CI/CD

Completed100 XP

-   40 minutes

**Estimated time:** 40 minutes.

**Lab files:** none.

## Scenario

In this lab, you'll learn how to implement a GitHub Action workflow that deploys an Azure web app using DevOps Starter.

## Objectives

After completing this lab, you'll be able to:

-   Implement a GitHub Action workflow for CI/CD.
-   Explain the basic characteristics of GitHub Action workflows.

## Requirements

-   This lab requires **Microsoft Edge** or an [Azure DevOps-supported browser](https://learn.microsoft.com/en-us/azure/devops/server/compatibility).
-   Identify an existing Azure subscription or create a new one.
-   Verify that you have a Microsoft or Azure AD account with the Contributor or the Owner role in the Azure subscription. For details, refer to [List Azure role assignments using the Azure portal](https://learn.microsoft.com/en-us/azure/active-directory/roles/manage-roles-portal).
-   If you don't already have a GitHub account that you can use for this lab, follow the instructions available at [Signing up for a new GitHub account](https://docs.github.com/get-started/signing-up-for-github/signing-up-for-a-new-github-account) to create one.