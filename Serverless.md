# Serverless

## History
Data Center -> IAAS -> PAAS -> Containers -> Serverless

## Lambda
* Lambda is a compute service
* upload code and create lambda function
* AWS Lambda takes care of provisioning and managing the servers
* Users don't need to worry about operating system, patching, scaling etc.

#### Example: 
* run lambda as an event-driven compute service
* run lambda as a compute service to response HTTP request using API gateway

### Support Languages
Node.js | Java | C# | Go | Python

### Pricing 
#### Request Numbers
* First 1 million request free
* $0.2 per 1 million request after 

#### Duration of processing
* calculate from time begins
* end returns / terminates
* round up the nearest 100ms

#### Memory
* depends on the amount of memory using
* $0.00001667 GB / second used

## Exam Tips
* Lambda scales out automatically
* Lambda functions are independent, 1 event = 1 function
* Lambda is serverless
* Lambda functions can trigger other lambda function
* Architecture can get extremely complicated
* AWS X-ray allows debug what is happening
* Lambda can do things globally

## Versioning 
* Can publish one or more versions of Lambda
* Can work with different variations of Lambda function in development flow
* Each Lambda function has a unique Amazon Resource Name (ARN)
* Publish a version, it is immutable (can not be changed)
* AWS Lambda maintain latest function code in $LATEST version
* When code is updated, Lambda replaces the code in $LATEST version

## Amazon Resource Name (ARN)
* Qualified ARN:
    function ARN with the version suffix:
        arn:aws:lambda:aws-region:accd-id:function:helloworld:$LATEST

* Unqualified ARN: 
    ARN without the version suffix

## Alias
create an alias name point a version lambda
change alias mapping
easy roll back

## Exam Tips
* Can have multiple versions of lambda functions
* Latest version will use $LATEST
* Qualified version will use $LATEST, Unqualified version will not have
* Can split traffic using alias to different versions
* Can not split traffic with $latest (need to create alias to $latest)

## Step Function
* Visualise
* Test serverless application
* Graphical console
* Arrange & visualise the components

Step function will automatically triggers and tracks each step, and retrys when there are errors.
Step function executes in order, and log the state of each step

