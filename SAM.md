# Serverless Application Model (SAM)
- an extension to CF used to define serverless applications
- Simplified syntax for defining serverless resources: APIs, Lambda Functions, Dynamo DB Tables etc.
- Use the SAM CLI package deployment code, upload to S3 and deploy serverless application 

## Command 
sam package \ 
    --template-file x \
    --output-template-file x \
    --s3-bucket x

sam deploy \ 
    -- template-file x \
    -- stack-name x \
    -- capabilities x

Transform: AWS::Serverless-2016-10-31

## CF Nested Stacks
- allow re-use of CloudFormation code for common use case
- create a standard template for each common use case
- reference from within CF template 

## Structure
Resources:
    Type: AWS::CloudFormation::Stack
    TemplateURL: https://s3.amazonaws.com/.../template.yml

Really useful for frequently used configurations 

