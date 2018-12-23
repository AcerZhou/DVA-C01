# IAM - (Identity Access Management)

## General
* Manage Users
* Manage Users' level of access to the AWS Console

## Functions
* Centralised control of AWS accounts
* Shared control of AWS accounts 
* Granular permissions
* Identity Federation (Active Directory, Facebook, LinkedIn)
* Multifactor Authentication
* Provide temporary access for users/devices and services
* Set up password rotation policy
* Integrate with many different AWS serivces
* Support PCI DSS Compliance

## Elements
Users - End users (people) <br>
Groups - Collection of users, under one set of permissions <br>
Roles - A set of permissions, assign to AWS resources <br>
Policies - Document, defines one (or more) permissions

# Group
* Logical group - build group based on logic, example: accountants, finance, markerting
* Group by group (?)

# User
When create user, can give user access type <br>
* Programmatic Access - Access Key ID & Secret Access Key | AWS API | CLI | SDK
* AWS Management Console Access - using password to access AWS console

# Role
* IAM Roles are a secure way to grant permissions to trusted entities
* Entities Can include
    - IAM User in another account
    - Application code running on EC2, and the code need perform actions on AWS resources
    - AWS Service needs to act on resources to provide features
    - Users from a corporate directory who use Identity Federation with SAML

## Other Important Point
* IAM is universal, does not apply to regions
* Root Account - created when first time set up AWS account, complete Admin access
* New users have no permissions when first created
* New users with Programmatic Access will be assigned Access Key ID & Secret Access Key when first created
* Access Key ID & Secret Access Key can only be viewed once. If lost, can regenerated. 

