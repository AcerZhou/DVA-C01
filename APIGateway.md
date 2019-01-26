# API Gateway

## API
* Application Programming Interface
* Type:
    - REST API
    - SOAP API

## Definition
API Gateway is a fully managed service that makes it easy for developers to publish, maintain, monitor
and secure APIs at any scale.

## Functions
* Expose HTTPS endpoints to define a RESTful API
* Serverless-ly connect to service like Lambda & DynamoDB
* Send each API endpoint to a different target
* Run efficiently with low cost
* Scale effortlessly
* Track and control usage by API key
* Throttle requests to prevent attacks
* Connect to cloudwatch to log all requests for monitoring
* Maintain multiple versions of API

## Configure API Gateway
1. Define an API (container)
2. Define resources and nested resources (URL paths)
    For each resources:
        - Select supported HTTP methods (verbs)
        - Set Security
        - Choose Target (such as EC2, Lambda, DynamoDB)
        - Set request and response transformations
3. Deploy API to a Stage
    - Use API Gateway default domain
    - Can use custom domain
    - Now support AWS Certificate Manager (free SSL/TLS certs)

## API Caching
API Gateway can enable to cache endpoint's response, it can reduce the number of calls to endpoint.
It can improve the latency of the requests

When caching is enabled for stage, API Gateway caches responses for a specific TTL (in seconds)

API Gateway looks up endpoint responses from cache instead of to end point.

## Same Origin Policy
Same Origin Policy is an important concept in the web application security model.

If two web pages have same origin, web browser permits scripts in the first page can access second page data.

This is to prevent Cross-Site Scripting (XSS) attacks.

This is enforced by web browser.
This is ignored by PostMan & Curl

## Cross-Origin Resource Sharing (CORS)
* One way
* Server at the other end can relax the same-origin policy

CORS is a mechanism. 
It allows restricted resource on a web pages to be requested from another domain outside 
the domain from the first resource was served

* Steps:
1. Browser makes an HTTP OPTIONs call for an URL
2. Server returns "These other domains are approved to GET this URL"

* Error:
"Origin policy can not be read at the remote resources" - Need to enable CORS on API Gateway

## API Gateway Features
* Low cost 
* Scale Automatically

## Import API into API Gateway
* API Gateway supports swagger v2.0 definition files

### Way to create API
- Submit a POST request that includes a swagger definition in the payload and endpoint configuration
- Update existing API using a PUT request that contains a swagger definition in the payload

Update an API by overwriting it with a new definition
Merge a definition with an existing API
Specify the options using a mode query parameter in the request URL

## API Throttling
* API limits the steady-state request rate to 10,000 request per second
* The maximum concurrent requests is 5,000 requests across all APIs with an AWS account
* Over throttling, client will receive 429 - Too many request error

## API Gateway - SOAP web service pass through