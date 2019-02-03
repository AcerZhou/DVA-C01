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

## Some thinking about IAM
* Least Privilage - give users the minimum amount of access required
* Create Group - assign users to groups 
    - users automatically inherit permission
    - policay documents give permissions to the group
* Secret Access Key - only can be seen once
    - delete and regenerate to create new one
    - if the secret access key changed, need to run aws configuration again
    - So, should give each developer their own access key, don't share one access key
* Roles are better options
    - allow user access resource without Access Key IDs and Secret Access Keys
    - roles are prefered from a security perspective
    - roles are contorlled by policies
    - updating on roles will affect immediately 
    - can attach or detach roles on running EC2 instances without shop or termination

## IAM 3 types of policies 
* Managed Policies 
* Customer Managed Policies
* Inline Policies

### Managed Policies
- an IAM policy created and administrated by AWS
- For common use cases based on job function 
- Allow assign appropriate permissions to users, groups, and roles without having to write the policy yourself
- A single managed policy can be attached to multiple users, groups, or roles within the same AWS account and across different accounts
- AWS Managed Policy's permission definition can not be changed 

### Customer Managed Policies
- a standalone policy
- User create and administer inside own AWS account 
- The policy can be attached to multiple users, groups, and roles, only within own account
- Can be created based on Managed Policy and customise it to fit the requirements of the organisation
- Recommended use cases where Managed Policy dont meet the needs of environment

### Inline Policy
- IAM policy which is actually embedded within the user, group, or role to which it applies
- This is a strict 1:1 relationship between the entity and the policy
- When the user, group, role are being deleted, inline policy will be deleted as well
- AWS recommends using Managed Policy over Inline Policy
- Inline Policy are useful when the policy should only be applied on single user, group, or role

