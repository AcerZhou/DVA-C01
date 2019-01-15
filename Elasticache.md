# Elasticache
* Used to significantly improve latency and throughput
* For read-heavy application workloads or compute-intensive workloads
* Improve application performance by storing critical
    - pieces of data in memory for low-latency access
    - result can have results of I/O intensive database queries
    - result of computationally-intensive calculations

## Type of Elasticache
* Memcached
* Redis

## Memcached
* A widely adopted memory object caching system
* Elasticache is protocol compliant with memcached
* Result of computationally-intensive calculations
* Elasticache manages memcached node as a pool that grow and shrink (similar to EC2 Auto Scaling Group)

### Memcached Character
* A pure caching solution with no persistence
* Individual nodes are expendable
* Elasticache provides additional capability (automatic node replacement & auto discovery)

### Memcached Use Case
* Object caching - offload DB
* As simple a caching model as possible
* Planning on running large cache nodes
* Require multi-threaded performance with utilization of multiple cores
* Scale cache horizontally

## Redis 
* A popular open-source in-memory key-value store
* Support data structure such as sorted sets or lists
* Master / Slave replication
* Multi-AZ can be achieved cross AZ redundancy
* Elasticache manages Redis more as a relational DB, because of replication & persistance features

### Redis Use Case
* Advanced data types (list, hashes, sets)
* Sorting and ranking data sets in memory (leader boards)
* Persistance of key store important
* Run in multiple AWS Multi-AZ with fail-over
* Pub/Sub capacities

### Redis Cluster
* Managed as stateful entities
* Include failover
* Similar to RDS

## Difference 
* Redis support Multi-AZ, Memcached not support 

## Similarity
* Both of them is similar in surface both in-memory key stores

## Difference between Elasticache & Redshift
### Elasticache
* For read-heavy program 
* Not prone to frequent changing

### Redshift
* Feeling stress because management keep running OLAP
* Can encrypt additional attached volumes using console, CLI or API (? need to review)