# RDS - Relational Database Service

## AWS RDS Support Database Type
| SQL Server | Oracle | MySQL Server | Postgre SQL | Aurora | Maria DB | 

## Special Point
* RDS only deal with DNS name, the mapping is contorlled by AWS

## Data Warehouse 
* BI - Business Intelligence

## OLTP vs. OLAP 
* Type of queries is different for two types of system
* RDS - OLTP
* Redshift - OLAP

## Back Up
* Automated Backups
* Database Snapshots

### Automated Backups
* Recover database to any point in time with a "retention period"
* Retention Period: 1 - 35 days
* Take a fully daily snapshot
* Store transaction logs throught the day
* When recovery, choose most recent daily back up and apply transaction logs
* To do a point in time recovery down to a second within the retention period
* Enable by default
* Stored in S3
* Free Storage space equal to size of DB
* Taken with a defined window
* In the window, storage I/O may be suspended (May experience elevated latency)
* Backups will be deleted, if RDS is deleted

### Snaphots
* Done manually - User initiated
* Store even deleted the original RDS instance

## Restoring Backups
* It will create a new RDS instance with a new DNS endpoint

## Encrypthon
* Encryption at rest is supported for 
    - MYSQL
    - Oracle
    - SQL Server 
    - Postgre SQL
    - Maria DB
    - Aurora
* Using AWS KMS
* RDS instance encrypeted, data stored at rest in the underlying storage is encrypted
* Same as automated backups, read replicas, and snapshots

* Encryption existing DB Instance is not supported
* To encrypt existing DB, must create a snapshot first, and make a copy of the snapshot, and encrypt the copy

## Multi-AZ (Synchronous)
* Have an exact copy of product database
* The database is in another Availability Zone
* AWS handles the replication
* The write will automatically be synchronized to the stand by database
* In the event of planned DB maintenance, DB Instance failure or Availability Zone failure, AWS will automatically fall over the stand by.
* DB operations can resume quickly without administrative intervention
* Multi-AZ for Disaster Recovery only
* Aurora build in Multi-AZ 
* Support Multi-AZ:
    - SQL Server 
    - MySQL
    - Postgre SQL
    - Maria DB
    - Oracle

## Read Replica (Asynchronous)
* A read-only copy of production DB
* Asynchronous replication from primary RDs instance to the read replica
* For read-heavy DB workloads
* Used for scaling
* Support read replica
    - MySQL
    - Postgre SQL
    - Maria DB
    - Aurora
* To deploy a read replica, the automatic backups must be turned on
* There is up to 5 read replica copies of any DB
* Can do a read replica of read replica (watch for latency)
* Each read replica have its own replica DNS end point
* Can have read replicas that have multi-AZ
* Can create read replicas of Multi-ZA source DB
* Read replicas can be promoted to their own DB (this breaks the replication)
* Read replica can be in another region For MySQL & Maria DB



