# Kinesis

## Streaming data 
- data is generated continuously by thousands of data sources
- data is sent simultaneously
- data is in small size (order of kilobytes)

## Kinesis
- A platform on AWS send streaming data 
- Make it easy to load and analyse streaming data
- Custom application for business needs

## Core Kinesis Service
* Kinesis Streams
* Kinesis Firehose
* Kinesis Analytics

### Kinesis Streams

Producers ----> Kinesis Stream (multiple shards) ---> Consumer

Kinesis Stream consist of shards
* Read : 5 transactions per second (up to maximum total data 2 MB/s)
* Write : up to 1,000 records per second / up to maximum total data 1 MB/s (including partition keys)
* data capacity of stream is a function of number of shards specified for the stream
* Total capacity if the sum of the shards

### Kinesis Firehose 
Using lambda analysis

automate way doing kinesis

### Kinesis Analytics
running the queries on Stream / Firehose

## Use cases
- Video Stream : securely stream video from connected devices to AWS for Analytics & ML
- Data stream : build custom applications process data in real-time

Lambda can be configured to subscribe a kinesis stream and execute when there is a new record, before sending the processed data on its final destination


