# AWS Key Management Service (KMS)
- is a managed service 
- make it easy to create and control the encryption keys used to encrypt data 

* Encryption keys need to be in the same region with the service

### Integrated Service 
| EBS | S3 | Red Shift | Amazon Elastic Transcended(?) | WorKMail | RDS |

## The Customer Master Key (CMK) - Regional
* alias
* creation data
* description
* key state
* key material (customer provided/ AWS provided)

KMS can never be exported 

KMS - Multi-tented hardware
Cloud SHM - Hardware only for customer who use it

## permissions
* Administrative Permissions
    - IAM Users/Roles manage the key 

* Usage Permissions 
    - IAM Users/Role use the key

## KMS API Calls 
* Can add external account to use key in KMS
* KMS key rotation for a year 

```
aws kms encrypt

aws kms decrypt

aws kms re-encrypt

aws kms enable-key-rotation
```

## KMS Envelope Encryption 

Encryption: 

KMS Master Key ---(Encrypts) --> Envelope Key (Data key) ----> Data

Decryption: 

KMS Master key + Encrypted Data Key  ---> Encryption Algorithm ---> Plain Text Data Key  --> Decrypted Data


## KMS Key Deletion 
* Can not delete the key immediately
* Schedule deletion, and it will be deleted in 7 to 30 days

