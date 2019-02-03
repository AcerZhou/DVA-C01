# Web Identity Federation (WIF)
- give uses access to AWS Resources after they have successfully authenticated with a web-based identity provider (eg. Amazon, Facebook, Google)
- Following successful authentication, the user receives an authentication code from the Web ID provider, which they can trade for temporary AWS security credentials

## AWS Cognito provides Web Identify Federation
* Sing-up and Sign-in to apps
* Access for guest users
* Act as an Identity Broker between web application and Web ID provider 
* Synchronise user data for multiple devices
* Recommended for all mobile applications AWS Service

Cognito brokers between the app and Facebook or Google to provide temporary credentials which map to an IAM role allowing access to the required resources.

No need for the application to embed or store AWS credentials locally on the device and it gives users a seamless experience across all mobile devices.

## Cognito User Pools
- User directories used to manage sign-up and sign-in functionally for mobile and web applications 
- User can sign-in directly to the User Pool, or indirectly via an identity provider (like Facebook, Amazon, or Google)
- Cognito acts as an Identity Broker between the ID provider and AWS
- Successful authentication generates a number of JSON Web Tokens (JWTs)

## Identity Pools
- to create unique identities for users
- authenticate users with identity providers
- with an identity, user can be enabled to obtain temporary, limited-privilege AWS credentials to access other AWS services

Cognito tracks the association between user identity and various different devices they sign-in from.

Cognito use Push Synchronisation to push updates and synchronise user data across multiple devices, to provide a seamless user experience

Amazon SNS is used to send a silent push notification to all the devices associated with a given user identity whenever data stored in the cloud changes

