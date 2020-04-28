# Zip and Publish to Azure Storage

[![Build Status](https://dev.azure.com/yardbirdsax/Azure%20DevOps%20Templates/_apis/build/status/zip-and-publish-azure-storage?branchName=master)](https://dev.azure.com/yardbirdsax/Azure%20DevOps%20Templates/_build/latest?definitionId=6&branchName=master)

This task template zips files at a given path and then pushes the resulting ZIP file to a designated Azure Storage Account.

## Pre-Requisites

* You must have an Azure Storage Account created in an active Azure Subscription.
* You must have an Azure Resource Manager Service Connection created in the Azure DevOps project where you'll be using this task. See [this documentation for details](https://docs.microsoft.com/en-us/azure/devops/pipelines/library/service-endpoints?view=azure-devops&tabs=yaml#sep-azure-resource-manager).
* The Service Principal used for the Service Connection must have the [Storage Blob Contributor](https://docs.microsoft.com/en-us/azure/devops/pipelines/library/service-endpoints?view=azure-devops&tabs=yaml#sep-github) role at the level of the Storage Account, which allows it to read / write data in the Account.
* You must have a GitHub Service Connection set up (to reference the template file in this GitHub repository). See [this documentation for details](https://docs.microsoft.com/en-us/azure/devops/pipelines/library/service-endpoints?view=azure-devops&tabs=yaml#sep-github).

## Usage

See the [example pipeline](examples/pipeline.yaml) for a sample of how to reference and use the template. Pay particular attention to these sections:

* **Resources.Repositories** - This is required to use the template, and is a reference to the GitHub repository where the template resides.
* **Steps.Template** - This is where you reference the actual template file.

## Parameters

The template accepts the following parameters.

| Name                  | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| sourcePath            | The root path for the Zip step. An files under this path will be compressed.|
| archiveFileName       | The name (including path if desired) of the archive file to create.         |
| azureConnectionName   | The name of the Azure Resource Manager Service Connection to use.           |
| storageAccountName    | The name of the Azure Storage Account to upload files to.                   |
| storageAccountContainerName | The name of the Container in the Storage Account where files will be uploaded to. |
| storageAccountPath    | The path under the Container where files will be placed.                    |

