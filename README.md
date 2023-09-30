# AzureCiNodeJS.ado
This templates uses the nodeJS framework for ci Pipeline. It also enables Snyk scan and Sonar scan into the pipeline

# ApiAndApiManagementVariables.

## Pipeline Requirements

The ci pipeline requires the following parameters to be defined:
Paramaters:


| Name  | type | Default | Values | Opional/Required | Comments |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| appDeploymentTarget | string | | | Required | |
| key | string | | | Required | |


These parameters provide multiple use case options for the pipeline, enable/disable flags for the utilization of different templates as per the requirements.


## Use Cases

You can directly call a particular template as per the requirement. for example: 

  ```yaml
  # azure-pipeline.yml
  resources:
  repositories:
    - repository: Template
      type: github
      name: your_username/AzureCiNodeJS.yml@Template
      ref: <respective branch name>
      endpoint: 'githubServiceConnectioNname'

jobs:
- job: CI
  displayName: "Run lint, build"
  steps:
  - template: templates/setApiAndApiManagementVariables.yml
        parameters:
          ${{ insert }}: ${{ parameters }}
  
Make sure to adjust the repository name, branch name, and parameter values according to your project's requirements.

  ```
