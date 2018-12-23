# ELB - Elastic Load Balancer

## Type 
* Application Load Balancer - Can load balance OSI layer 7 application
* Network Load Balancer - Can load balance OSI layer 4, Speed Improvement
* Classtic Load Balancer - Classic, used to be load balancer in AWS

### Application Load Balancer
* Can manager HTTP & HTTPS traffic
* Working on OSI layer 7 and can be application-aware
* Intelligent
* Can create advanced request routing

### Network Load Balancer
* Manager TCP traffic
* Having extreme performance
* Working on connection level 4
* Can handling millions of requests per second
* ultra low latencies
* most expensive 

### Classic Load Balancer
* Legacy Elastic Load Balancer
* HTTP / HTTPS applications
* Having Layer 7 specific features ( X-Forward & Sticky Session)
* Strict Layer 4 load balancing (applications that purely rely on the TCP Protocol)

### Trouble Shooting
* If application stops responding, ELB will responds with HTTP Code 504

### X-Forward
* Since using load balancer, it is hard to find the original ip address.
* From application's view, all come from load balancer
* Can use X-Forward solve the problem
* using X-Forwarded-For Header to get original IP Address

