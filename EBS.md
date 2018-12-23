# EBS - Elastic Block Storage

## Function
* Create storage volumes 
* Attach to EC2 instances

## Special Points
* Placed in a specific Availability Zone
* Automatically replicated to protect from single point of failure

## Type
* General Purpose SSD (GP2)
    - Genearl purpose
    - Price & performance balance
    - From 3 IOPS - 10,000 IOPS

* Provisioned IOPS SSD (IOI)
    - I/O intensive applications
    - For large relational DB or NoSQL DB
    - More then 10,000 IOPS

* Throughput Optimized HDD (ST1)
    - Big DAta, DW, Log processing
    - Can not be the boot volume 

* Cold HDD (SC1)
    - Lowest cost storage for infrequently accessed
    - File Server 
    - Can not be the boot volumne

* Magnetic (Standard)
    - Lowest cost per gigabyte in bootable
    - Workload that data is accessed infrequently
    - Application lowest storage
