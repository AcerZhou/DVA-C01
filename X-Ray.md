# AWS X-Ray
* is a service
* collects data about requests that application serve
* provides tools can view and filter
* gain insights into data
* to identify issues and opportunities for optimization
* detail information about request & response
* downstream AWS resources, microservices, databases and HTTP Web APIs


## AWS X-Ray Architecture

X-Ray SDK ---> X-Ray Daemon ---> X-Ray API ---> X-Ray Console

AWS SDK & CLI --> X-Ray Daemon 

AWS SDK & CLI --> X-Ray API

## AWS X-Ray SDK
* Interceptors
* Trace incoming HTTP request
* Client handles to instrument AWS SDK client 
* Application uses to call other AWS services
* HTTP client to use to instrument calls to other internal & external HTTP Web Service

## Service can integrates with X-Ray
* Elastic Load Balancing (ELB)
* AWS Lambda
* Amazon API Gateway
* Amazon Elastic Compute Cloud (EC2)
* AWS Elastic Beanstalk

## Language Support
* JAVA 
* Node
* Go
* Python
* .Net

