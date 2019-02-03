# Cloud Formation 
- A service that allows user manage, configure and provision AWS Infrastructure as Code
- Resources are defined using a CloudFormation Template
- CloudFormation interprets the template and makes appropriate API calls to create the resource
- Support YAML and JSON

## Benefits 
* Infrastructure is provisioned consistently, with fewer mistakes
* Less time and effort than configuring things manually
* Version control and peer review templates
* Free to use (charged for what you create)
* Can use manage updates & dependencies 
* Can rollback and delete entire stack 

## CloudFormation Template
* JSON/YAML
* upload to CloudFormation using S3
* CF read template & make API calls
* The resulting resources are called a Stack

### CloudFormation Template Example

AWSTemplateFormatVersion: "2010-09-09"
Description:
Metadata:
Parameters: # input value
Conditions: 
Mappings: # set values based on a region
Transform: # include snippets of code outside the main template
Resources: # the AWS Resources you are deploying 
Outputs:

* Resources is the only mandatory section of CF
* Transform section is used to reference additional code stored in S3, allowing for code re-use