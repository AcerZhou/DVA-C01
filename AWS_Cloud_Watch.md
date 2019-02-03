# AWS Cloud Watch
- a monitoring service to monitor AWS Resources and application on AWS

## EC2 Host Level Metrics Consist of 
* CPU
* Network
* Disk
* Status Check

RAM Utilisation is a custom metric

By default, EC2 monitoring is 5 minutes intervals. 
If enable detail monitoring, interval becomes 1 minute.

## How long are Cloud Watch Metrics Stored
- can retrieve data using GetMetricStatistics API
- use third party tools offered by AWS partners
- log data can be stored in AWS indefinitely
- User can choose the time storing log data
- data can be retrieved for terminated EC2 or ELB instance after its termination 

## Metric Granularity
- depends on AWS service
- many default service are 1 min, but it can be 3 or 5 mins
- Minimum Granularity for CloudWatch is 1 minute

Cloud Watch can be sued ton premise

## CloudWatch vs Cloud Trail vs Config
* CloudWatch monitor performance
* Cloud Trail monitors API calls in the AWS platform
* Config records the state of AWS environment can notify changes
