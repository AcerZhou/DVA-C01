# Elasticache
- in-memory cache in the cloud
- retrieve information from fast in-memory caches rather than slower disk based database
- generally sit between application and database
- takes the load off database
- for read-heavy application and data not change frequently

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
* Multi-thread
* No Multi-AZ capability

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

## Caching Strategy
* Lazy Loading
* Write-Through

### Lazy Loading
- loads the data into cache only when necessary
- if data is in cache, will be return
- if data is not in cache, return null
- fetches data from the database, and writes data received into the cache


| Advantages                 | Disadvantages      |
| Only requested data cached | Cache miss penalty |
| Node failure is not fatal  | Stale data         |

* Stale data - if data has changed in database, it will not automatically updated

#### Time to Live - TTL
- specified the number of seconds until data(key) expires
- avoid keeping stale data in the cache

* Lazy loading treat expired key as a cache miss.
    - it will retrieve data from DB
    - write data into cache and give it a new TTL

* TTL does not eliminate stale data, but it helps to avoid it 

### Write Through
- adds or update data to the cache whenever data is written to the database

| Advantages       | Disadvantages    | 
| Data never stale | Write penalty    |
| User tolerant    | Node failure     | 
|                  | Wasted resources |

* User tolerant : users are more tolerant when updating data then retrieving it
* Node failure : if the node failure, the cache data will be only available after adding or updating (can implement with lazy loading)
* wasted resources : if most of data is never read

