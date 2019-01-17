# CloudFront

## CDN (Content Delivery Network)
* A system of distributed servers (network)
* deliver web pages and other web content
* to a user based on the geographic locations 
* user/origin of the web page/delivery server
* Focus on content delivery - download

* Edge Location & Cache
* User can clear cache, but will be charged

## Edge Location
* Location where content is cached
* Can also be written
* Separated to an AWS region/AZ

## Origin
* Can be S3 bucket, EC2 Instance, Elastic Load Balancer, Route 53

## Distribution
* name given the CDN
* have a collection of Edge Location

Web Distribution: For Web Site - (HTTP/HTTPS)
RIMP - for Media streaming (Adobe Real Time Messaging Protocol)

## Cloud Front
* Can be used to deliver entire website
* Dynamic, Static, Streaming and interactive content
* Using a global network of edge locations

* For best performance, request will be automatically routed to the nearest edge location
* Work seamlessly with non-AWS origin server