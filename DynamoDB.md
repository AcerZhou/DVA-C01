# Dynamo DB - serverless
- A fast and flexible NoSQL database service
- Consistent, single-digit millisecond latency at any scale
- Fully managed database
- Support both document and key-value data model
- Store on SSD
- Spread across 3 geographically distinct data centre

## Dynamo DB use case 
* Mobile
* Web
* Gaming 
* Ad-Tech
* IoT

## Consistency models
- Eventual Consistent Reads (Default)
- Strongly Consistent Reads

## Eventual Consistent Reads (Best Read Performance)
- Consistency across all copies of data
- Reached with in a second
- Repeating a read after a short time should return the updated data

## Strongly Consistent Reads
- Returns a result 
- Reflects all writes that received a successful response prior to the read

## Dynamo DB 
- Table 
- Items
- Attributes

* Documents can be written in JSON, HTML, XML

## Dynamo DB Primary Keys
- Stores and retrieves data
- based on a Primary Key

## Partition key - unique attribute
- value of the Partition key is input to a internal hash function
- determines the partition or physical location on which data is stored
- no two items can have the same partition key

### Composite Key - (Partition key + Sort key)
- is a combination
- two items may have same partition key, but they must have different sort key
- all items with same partition key are stored together, then sorted according to the sort key value
- allow store multiple items with same partition key

## Access Control & Authentication
- managed by IAM

* Can create an IAM user within AWS account has specific permissions to access & create DynamoDB tables
* Can create an IAM role, obtain temporary access keys access Dynamo DB

* Can use a special IAM condition to restrict user access to only their own records
Example: Adding a condition to an IAM policy to allow access to items (partition key match User Id)

## Index
- a data structure
- perform fast queries on specific columns in a table

### Type of Index
* Local Secondary Index
* Global Secondary Index

### Local Secondary Index
- is only create when create table
- can not add, remove, or modify it later
- has same partition key as original table 
- has different sort key
- organised according to an alternative sort key
- any queries based on this sort key are much faster using index then the main table

### Global Secondary Index
- can create when create table or add later
- has different partition key
- has different sort key
- give a completely different view of the data
- speed up any queries relating to this alternative partition key and sort key

## Scan & Query API call

### Query
- find items in a table based on the primary key attribute and a distinct value to search for
- use an optional sort key name and value to refine the results
- by default, query returns all the attributes for items
- use Projection Expression parameter to query specific attribute
- results are always sorted by the sort key
- numeric order is by default ascending
- ASCII char code values (?)
- using Scan/Index Forward parameter to reverse order
- queries are Eventually Consistent by default and can be set to Strongly Consistent

### Scan
- examines every item in the table
- return all data attribute by default
- can also use Scan/Index Forward Parameter to refine the scan only return attributes specific

#### Detail of Scan
* Scan operation processed data sequentially in returning 1 MB data before moving on to retrieve the next 1 MB data
* Scan can only scan one partition at a time

#### Parallel Scan
* DynamoDB can be configured to use Parallel scan
* Logically dividing a table or index into segments and scanning each segments in parallel

### Comparison
* Query is more efficient than Scan
* Scan dumps the entire table, then filter out values 
    - table grows, scan will take longer
* Scan operation on a large table can use up the provisioned throughput for a large table in just a single operation

## Improve Performance
* Setting a smaller page size can reduce the impact of a query or scan
* Large number of smaller operations will allow other requests to succeed without throttling
* Avoid scan operation
* Design table in a way using query, Get, BatchGetItem APIs
* Best of avoid parallel scans if table or index is already incurring heavy read/write activity from other applications
* Parallel can heavily affect other operations

## Provisioned Throughput
- Measured in capacity units
When creating table, specify read capacity units and write capacity units 

```
1 Write Capacity Unit = 1 * 1 KB/S Write

1 Read Capacity Unit = 1 * 4 KB/S Strongly Consistent Read

1 Read Capacity Unit = 2 * 4 KB/S Eventual Consistent Read

```

If application reads or writes larger items, it will consume more capacity units and will cost more

* When calculate Read & Write capacity units, need to round the number

## Dynamo DB On-Demand Capacity (New Feature)
- affect reading, writing and storing data
- Instantly scales up and down based on application activity
- it is designed for unpredictable workloads
- pay for use
- change once per day

## Dynamo DB Accelerator (DAX) - For Read only
- fully managed, clustered in-memory cache for DynamoDB
- reduce read load on DynamoDB tables for Read-Heavy and bursts workloads
- maybe able to reduce provisioned Read Capacity

* Delivers up to a 10x read performance improvement
* Microsecond performance for millions of requests per second
* Using Write-Through Strategy

### Detail for DAX
DAX is a write - through caching service 
    - data is written to the cache 
    - written to the back end store at same time
* Allow point DynamoDB API calls the DAX cluster

### Process
* If cache hit, DAX returns the result 
* If cache miss, DAX performs an Eventually Consistent GetItem operation, and write to DAX

### Use Cases
* Application work with Eventually Consistent Read
* Application is not write intensive 
* Application needs to perform many read operations
* Application require microsecond response times

## Dynamo DB Transactions

### ACID Transactions
- Atomic
- Consistent
- Isolated
- Durable

* Read or Write multiple items across multiple tables as an all or nothing operation
* Check for pre-requisite condition before writing to a table

## Dynamo DB TTL 
- TTL attribute defines an expire time for data
- Expired items marked for deletion
- Used to remove irrelevant or old data (session data, event logs, temporary data)
- Reduces cost by automatically removing data which is no longer relevant
- TTL expressed as epoch time (Unix Time)

### Process
When the current time is greater then the TTL, the item will be expired and marked for deletion

Can filter out expired items from query and scan

Expiration is set for 2 hours after the session begin.

With 24 hours from marked for deletion, record will be removed. 

## Dynamo DB Streams
- Time-ordered sequence of item level modifications (insert, update, delete)
- Logs are encrypted at rest and stored for 24 hours
- Accessed using a dedicated endpoint
- By default the primary key is recorded
- Before and after images can be captured
- Event are recorded in neal real-time
- Applications can take actions based on contents 
- Event source for Lambda 
- Lambda pulls the DynamoDB streams
- Executes Lambda code based on a DynamoDB stream event

## Provisioned Throughput Exceeded & Exponential Back off (?)
* Provisioned throughput exceeded exception
* Request rate is too high for read/write capacity provisioned on the DynamoDB table
* SDK will automatically retries the requests until successful

### Exponential Back Off
Many components in a network can generate errors due to being overloaded 

All AWS SDK use Exponential Back Off

Progressively longer waits between consecutive retries

If after 1 min still not working, request size my be exceeding the throughput for read/write capacity 