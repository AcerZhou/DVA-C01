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