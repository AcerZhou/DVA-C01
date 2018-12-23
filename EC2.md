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

### Dedicated Hosts
* Regulatory requirements that may not support multitenant virtualisation (have to have because of regulation)
* Licensing that does not support multi-tenancy or cloud deployments (have licensing that can not apply to AWS EC2 resources)
* Can be purchased On Demand
* Can be purchased as a Reservation

