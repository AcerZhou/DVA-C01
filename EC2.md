# EC2 - Amazon Elastic Compute Cloud

## Definition
A web service that provides resizable compute capacity in the cloud

## Benefit
* Reduce obtain
* Boot new server instances to mins
* Allow quick scale up & down, and out

## Price Model
* On Demand - Fixed rate per hour (or second)
* Reserved - Capacity reservation, fix term contract (1 or 3 years)
* Spot - Bid whatever price you want (?)
* Dedicated Hosts - Have dedicated EC2 instances

### On Demand Instances
* Low cost & Flexibility of Amazon EC2
* No up-front payment or long-term commitment
* Good for application with short term, spiky or unpredictable workloads
* Good for applicaiton being developed or tested

### Reserved Instances
* Steady state or predictable usage
* Reserved capacity
* Up-front payments to reducing computing cost
    - Standard RLs (75%)
    - Convertible RLs (54%)
    - Scheduled RLs 

### Spot Instances (?)
* Flexible start and end times
* Feasible at very low compute prices
* urgent need for large amounts of additional computing capacity

* If spot instance is terminated by Amazon EC2, not charge for the partical hour of usasge
* If spot instance is terminated by user, will be chared for completed hour

### Dedicated Hosts
* Regulatory requirements that may not support multitenant virtualisation (have to have because of regulation)
* Licensing that does not support multi-tenancy or cloud deployments (have licensing that can not apply to AWS EC2 resources)
* Can be purchased On Demand
* Can be purchased as a Reservation

### Type of EC2

| Family | Speciality                     | Use Case                                |
| ------ | ------------------------------ | --------------------------------------- |
|   F1   | Field Programmable Gate Array  | Genomics Reasearch, Financial Analytics | 
|   I3   | High Speed Storage             | NoSQL DBs, DW etc.                      | 
|   G3   | Graphics Intensive             | Video Encoding / 3D Application Stream  | 
|   H1   | High Disk Throughput           | Map Reduce-based work loads             | 
|   T2   | Lowest Cost, General Purpose   | Web Servers / Small DBs                 | 
|   D2   | Dense Storage                  | File Server / DW / Hadoop               | 
|   R4   | Memory Optimized               | Memory Intensive Apps / DBs             | 
|   M5   | General Purpose                | Application Servers                     | 
|   C5   | Compute Optimized              | CPU Intensive Apps                      | 
|   P3   | Graphics / General Purpose GPU | Machine Learning, Bit Coin              | 
|   X1   | Memory Optimised               | SAP HANA / Apache Spark                 | 

* FIGHT DR MCPX