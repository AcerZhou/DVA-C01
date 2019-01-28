# Simple Notification Service (SNS)
- is a web service
- easy to set up, operate and send notifications from the cloud
- highly scalable, flexible and cost-effective capability to publish messages from an application
- immediately deliver messages to subscribers or other application

## Push Notification
| Apple | Google | Fire OS | Windows | Android (China with Baidu push)

## SNS client
* Push to mobile device
* SMS text message
* Email to SQS 
* Any HTTP endpoint
* trigger Lambda function (invoke lambda with the payload as input)

## SNS Detail
- group multiple recipients using topics

* A topic is an "access point", allowing recipients to dynamically subscribe for identical copies of the same notifications

* One topic can support deliveries to multiple endpoint types

* When publish once to a topic, SNS delivers appropriately formatted copies of messages to each subscriber

* All messages published to Amazon SNS are stored redundantly across availability zones

* Follow "Publish - Subscribe" (pub-sub) messaging paradigm
* Push mechanism

## Benefits:
* Instantaneous, push-based delivery
* Simple API, Easy integration
* Flexible message delivery over multiple transport protocols
* Inexpensive, pay-as-you-go model with no up-front costs
* AWS Console, point and click interface

## Simple Email Service (SES)
- a scalable and highly available email service
- designed to help marketing teams & application developers

### Feature
- SNS can used to receive emails
- incoming email to S3 bucket
- SNS can trigger Lambda functions and SNS notifications

### Use cases
* Sending marketing notification and transactional emails to their customers using a pay-as-you-go model

Example:
* Automated emails
* Purchase confirmation
* Shipping notification
* Order status updates
* Marketing communications advertisements, newsletters and special offers


| SES                      | SNS                                               |
| Email messaging service  | Pub/Sub Messaging service (SMS, HTTP, SQS, Email) |
| Lambda                   | Lambda                                            |
| Incoming & outgoing email| Fan out message to large recipients               |
| A email address required | Consumer must subscribe a topic                   |

