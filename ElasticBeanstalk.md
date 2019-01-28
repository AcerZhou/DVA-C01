# Elastic Beanstalk 
- A service for deploying and scaling web applications
- makes developer can focus on writing code and don't worry about underlying infrastructure

## Support Server platform & Languages
* Application Server Platforms
| Apache Tomcat | Nginx | Passenger | IIS |

* Language:
| Java | .Net | PHP | Node.js | Python | Ruby | Go | Docker |

## Elastic Beanstalk Features
- Elastic Beanstalk handle deployment, capacity provisioning, load balancing, auto-scaling and application health
- Developer retain full control of AWS resources and only pay for required to store and run application
- Fastest & Simplest way to deploy application to AWS 
- Automatically scales up & down
- User can have full control or have Elastic Beanstalk manage
- Managed platform updates feature automatically apply to Operating System
- Monitoring and managing via a dashboard
- Integrate with Cloud Watch & X-Ray for performance & metrics

## Elastic Beanstalk Deployment Policies

### Type of deployment policies
* All at once 
* Rolling
* Rolling with additional batch
* Immutable 

### All at once 
- Deploys the new version to all instances at same time

* All instances are out of services while deployment happens(having outage when deployment happens)
* If update fails, need to roll back the deployment and re-deploy the original version to all instances
* No good for mission-critical production system

### Rolling 
- Deploys the new version in batches, each batch of instances is taken out of service when deployment happens

* The capacity of environment will be reduced in batch when deployment happens
* If update fails, need an additional rolling update to roll back the changes
* Not good for performance sensitive systems

### Rolling with additional batch
- Deploys the new version in batches, and launch an additional batch of instances

* Maintain full capacity during the deployment process
* If update fails, need an additional rolling update to roll back the changes

### Immutable 
- Deploys the new version to a new group of instances, in their own auto scaling group
- When the new instances pass health check, they will be moved to auto scaling group and old instances are going to be terminated

* Maintains full capacity during deployment process
* The impact of failed update is minimum, roll back only terminate the new auto scaling group
* Prefer for mission critical production systems

## Configuring Elastic Beanstalk
- using JSON/ YAML configuration files to customise Elastic Beanstalk Environment
- config file must have .config extension
- config file need to saved into .ebextensions folder
- .ebextensions folder must be included in the top-level directory of application code source bundle
- config file can be place under source control along with the rest of application code

## RDS & Elastic Beanstalk
- Elastic Beanstalk supports two ways of integrating with RDS

* Launch RDS instance with Elastic Beanstalk console
    - Good for Dev and Test environment
    - Not good for Production environment
    - This is because that the lifecycle of DB is tied to the lifecycle of application environment

* Launch RDS from RDS section
    - Decouple RDS & Elastic Beanstalk
    - Having more flexibility, more choices of DBs
    - Can tear down application environment without affecting the database instance

### Access RDS from Elastic Beanstalk
An additional security group must be added to auto scaling group and need to provide connection string configuration to application server