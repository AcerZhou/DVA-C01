# Simple Queue Service (SQS)
- A webservice gives access to a message queue
- Store messages when waiting to be processed
- A distributed queue system
- Enable web service applications quickly and reliably queue messages
- One component generates/ one component consumed
- A queue is a temporary repository for messages that are awaiting processing

* SQS is a pull based system

## SQS in Architecture
* Decouple the components of an application
* Components can run independently, easing message management between components
* Any component of distributed application can store messages in the queue
* Queue acts as a buffer between producer and processor
* Bring elasticity into architecture

## SQS Feature
* Message can contain up to 256 KB of text in any format
* Retrieve messages using Amazon SQS API programmatically
* Message can be kept in Queue from 1 min to 14 days (Default is 4 days)

## Queue Type 
* Standard Queue (default)
* FIFO Queue (First-In-First-Out)

### Standard Queue
- Having a nearly-unlimited number of transactions per second
- Guarantee a message at least delivered once
- However, because of the highly-distributed architecture that allow high throughput, more then one copy of a message might be delivered out of order
- Standard Queue provide best-effort ordering (generally delivered in the same order as they are sent)

### FIFO Queue
- First in First out delivery
- Exactly-once processing
- Order is restricted preserved
- Message is delivered once, and duplicate is not introduced
- Support message group (multiple ordered message groups within a single queue)
- Remain available until consumer process and delete
- Limit 300 transactions per second (TPS)
- Have all capacity of standard queue

## SQS Visibility Timeout
- amount of time that the message is invisible after a reader picks up the message

* If the job processed the message within timeout, message will be deleted from the queue
* If the job didn't processed the message within timeout, message will appear again

This could result in duplicate message

* SQS visibility timeout max can be 12 hours, and the default visibility timeout is 30 seconds

## SQS Long polling
- a way to retrieve message from SQS queue

* Regular short polling returns immediately. (Even if the message queue being polled is empty)

* Long polling doesn't return a response until a message arrives in the message queue Or long polling time out

* Long polling can save money

