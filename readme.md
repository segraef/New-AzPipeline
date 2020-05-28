# Programmatically create Azure Pipelines

This Functions lets you programmatically create Azure Pipelines based on your folder structure.
It browses through your folder structure for pipeline.yml files and creates corresponding Azure Pipelines in Azure DevOps.
It has several features like creating pipelines based on a specific folder/module version, latest version or just creates all.
It also compares against existing Pipelines and skips these.

## Parameters

**Mandatory**
- OrganizationName (Azure DevOps Organization)
- ProjectName (Azure DevOps Project)
- RepositoryName (Azure DevOps Repository)

**Optional**
- FolderPath (Azure Pipelines folder path)
- Version (Pipeline versions to be used)
- PipelinePath (Local folder path to be browsed)
- Latest (Latest Pipeline versions to be created)
- All (All Pipeline versions to be created)

## Usage

`.\New-AzPipeline.ps1 -OrganizationName <OrganizationName> -ProjectName <ProjectName> -RepositoryName <RepositoryName> -Latest`

## Requirements

- Azure DevOps Login (az devops login) or Azure Login (az login / Connect-AzAccount)
- Azure DevOps Organization
- Azure DevOps Project
- Azure DevOps Repository

## Permissions

Contributor (Azure DevOps)

## Base Folder Structure

```
root
 ┣ Module0
 ┃ ┗ 2020-04-20
 ┃ ┃ ┗ Pipeline
 ┃ ┃   ┣ pipeline.variables.yml
 ┃ ┃   ┗ pipeline.yml
 ┣ Module1
 ┃ ┣ 2020-01-09
 ┃ ┃ ┗ Pipeline
 ┃ ┃   ┣ pipeline.variables.yml
 ┃ ┃   ┗ pipeline.yml
 ┃ ┗ 2020-03-20
 ┃ ┃ ┗ Pipeline
 ┃ ┃   ┣ pipeline.variables.yml
 ┃ ┃   ┗ pipeline.yml
 ┃ .
 ┃ .
 ┗ New-AzPipeline.ps1
 ```

Based on this structure `New-AzPipeline.ps1` recognizes

- `Module0` and `Module1` as Pipeline names
- `2020-04-20` as corresponding versions
- Azure Pipelines based on `pipeline.yml`

## Impressions

![](.attachments/images/2020-05-28-16-50-18.png)

![](.attachments/images/2020-05-28-16-31-58.png)

![](.attachments/images/2020-05-28-16-27-23.png)

![](.attachments/images/2020-05-28-16-48-26.png)

## Contributions

 Thanks to [@simonbms](https://github.com/simonbms) for helping me out with the object comparions in order to have only the latest folders picked for the `-Latest` switch.