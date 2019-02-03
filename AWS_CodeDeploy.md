# AWS Code Deploy
- Automated Deployment Service
- Allow deploy application code automatically to EC2, on premise systems and Lambda functions

## Benefits
* Quick release new features
* Avoid downtime during application deployments
* Avoid risk associated with manual processes 
* Automatically scales with infrastructure & integrates with various CI/CD tools (eg. Jenkins, GitHub, Atlassian, AWS Code pipeline)

## Config Management Tools
Ansible | Pupet | Chef

## Deployment Approaches
* In-Place
* Blue/Green

### In-Place Deployment (Rolling Update)
* The application is stopped on each instance and latest revision installed
* During the time, the instance is out of service and capacity will be reduced
* If the instance is behind load balancer, can config stop sending request to the instance which is upgrading
* Only support EC2 & On-Premise system, not Lambda
* If roll back, previous version need to be redeployed

### Blue/Green Deployment
* New instances are provisioned
* Latest version is installed on the new instances 
* Blue: active deployment  | Green: new release
* New instances are registered with an Elastic Load Balancer, traffic then routed to the new instances, and original instances are eventually terminated 

#### Advantages
* New instances are created ahead of time code release by simply switching all traffic to new servers
* Switching back to original environment is faster and more reliable

## Code Deploy - Terminology
* Deployment Group
    - A set of EC2 instances or Lambda Functions
    - A new revision of the software is to be deployed

* Deployment
    - The process and components used to apply a new revision

* Deployment Configuration
    - A set of deployment rules
    - Success/ Failure conditions used during a deployment 

* AppSpec File
    - Deployment actions code deploy to execute

* Revision
    - Everything needed to deploy the new version
    - AppSpec file, Application file, Executables, Config files

* Application
    - Unique identifier for the deploy application
    - To ensure the correct combination of revision, deployment configuration, and deployment group are referenced during a deployment

## Advanced Code Deploy

### AppSpce File
- define the parameters that will be used for a Code Deploy deployment
- file structure depends on deploying to Lambda or EC2/On-Premises

#### AppSpec File - For Lambda 
- can use YAML or JSON 

version:
    - Reserved for future use
    - currently, only allow value is 0.0

resources:
    - name and properties of Lambda function to deploy

hooks:
    - specifies lambda run at set points in the deployment lifecycle to validate the deployment (eg. validation test run before allowing traffic to be sent to newly deployed instances)

Before Allow Traffic 
- Specify task or function runs before traffic is routed to the newly deployed Lambda Function (validate function has been deployed correctly)

After Allow Traffic
- Specify task or functions run after traffic has been routed to the newly deployed Lambda function (validate function accept traffic correctly and behaving as expected)

#### AppSpec File - EC2/On-Premises 
- only support YAML

version: 
    - reserved fro future use 

os:
    - operating system is using 

file: 
    - location of any application files need to be copied location should be copied to (source and destination folders)

hooks:
    - specify scripts need to run at set points in the deployment lifecycle (unzip application files prior the deployment, run functional tests on the newly deployed application, de-register and re-register instances with load balancer)

#### For EC2/On-Promises
appspec.yml must be placed in the root of the directory of your revision

Example: 
    folder:
        appspec.yml
        /Scripts
        /Config
        /Source

Hooks 
- BeforeBlockTraffic : run before de-register from LB
- BlockTraffic : de-register instance from LB
- AfterBlockTraffic : run after de-register from LB

- ApplicationStop : gracefully stop application preparing for deployment 
- DownloadBundle : code deploy agent copies the application revision to a temporary location

- BeforeInstall : pre-installation scripts
- Install : Code Deploy agent copies the application revision files from temporary location to corret location 
- AfterInstall : post-installation script

- ApplicationStart : restarts any service that were stopped during Application Stop 
- ValidateService : test to validate the service 

- BeforeAllowTraffic : test before register LB
- AllTraffic : register to LB
- AfterAllowTraffic : after register to LB