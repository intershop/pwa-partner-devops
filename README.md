
# pwa-partner-devops

## Overview

Repository *pwa-partner-devops* provides an *Azure DevOps Pipeline* template, which can be used by PWA projects, that are managed inside *Intershops Commerce Platform* The template should be used as is. Any custom additions should be made outside of the template.

## How to use the pipeline template

To use the pipeline template, add a file named `azure-pipelines.yml` to the root directory of your project with the following content:

```
# azure-pipelines.yml

resources:
  repositories:
    - repository: pwa-partner-devops
      type: github
      endpoint: <GitHub Connection>
      name: intershop/pwa-partner-devops
      ref: refs/heads/stable/v1

jobs:
  - template: ci-job-template.yml@pwa-partner-devops
    parameters:
      <PARAMETER>

```
A more detailed example can be found in the `azure-pipelines.yml.tmpl` file.
After that, in Azure DevOps a new pipeline has to be created from this file.

## Parameters

| Parameter Name | Description | Default Value | Required |
|---|---|---|---|
| id | Identifies each job uniquely when ci-job-template.yml is used in a loop. Can only contain characters, numbers, and underscores. Also used to extend names of files published in extensions. |  | No |
| dependsOn | Enables an easy integration with custom jobs. The parameter will be passed as is to the dependsOn property of the job. |  | No |
| condition | Enables an easy integration with custom jobs. The parameter will be passed as is to the condition property of the job. |  | No |
| agentPool | Specifies the name of the agent pool. |  | Yes |
| registryServiceConnection | Defines the service connection to the registry/ACR of the project. |  | Yes |
| registry | Specifies the repository in registry/ACR url. |  | Yes |
| projectPath | Specifies the name of the repository. | `$(Build.Repository.Name)` | Yes |
| predefinedImageTag | Specifies a predefined image tag. If not set, it will be generated by build ID or tag value. |  | No |
| predefinedImageName | Specifies a predefined image name. If not set, it will be generated by `System.CollectionUri`, `System.TeamProject` and `Build.SourceBranchName`. |  | No |
| ssrBaseImageName | Specifies the name of the predefined SSR container. | pwa-ssr | Yes |
| nginxBaseImageName | Specifies the name of the predefined Nginx container. | pwa-nginx | Yes |
| lockImages | Specify whether an image built based on a Git tag should be locked in the Azure container registry. | true | Yes |
| jobTimeoutInMinutes | Specifies the maximum job execution time in minutes. | 300 | Yes |
| jobContinueOnError | Specifies whether future jobs should run even if this job fails | false | Yes |

## Important information:

Always refer to the `stable/v1` branch or a tag as the main/master branch is under constant development and breaking changes cannot be excluded. The `stable/v1` represents a branch that is backward compatible and does not contain any breaking changes.
