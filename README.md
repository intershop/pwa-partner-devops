
# pwa-partner-devops

## Overview

Repository *pwa-partner-devops* provides an *Azure DevOps Pipeline* template, which can be used by PWA projects, that are managed inside *Intershops Commerce Platform*. The template should be used as is. Any custom additions should be made outside of the template.

## How to use the pipeline template

Add a file `azure-pipelines.yml` to the root-directory of your project with following content. After that, in Azure DevOps a new pipeline has to be created from this file.

## Important information:

Always refer to the `stable/v1` branch or a tag as the main/master branch is under constant development and breaking changes cannot be excluded. The `stable/v1` represents a branch that is backward compatible and does not contain any breaking changes.
