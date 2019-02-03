# Docker & Code Build

## Docker
Docker is an open source technology, and create applications based on Linux or Windows containers 

## Container 
- a lightweight standalone executable software package
- including everything that software needs to run (code runtime environment, libraries, environment settings)

## Elastic Container Service 
- a fully managed clustered platform
- allows run Docker images in the cloud

## Code Build
- a fully managed build service 
- runs a set of commands that defines

## Commands 
* Build Docker 
```
docker build -t [my_docker_repo]
```

* Tag Image
```
docker tag [my_docker_repo]:latest x.dkr.ecr.region.arn...
```

* Push Image
```
docker push x.dkr.ecr...
```

## Code Build
buildspec.yml
    version: 
    env: 
    phases:
        pre_build:
            commands:
        build:
            commands:
        post_build:
            commands:

* Build specification 
- can use buildspec.yml
- can insert build command

## Exam Tips
* Docker Commands to build, tag (apply an alias) and push Docker Images to the ECR repository
* Use buildspec.yml to define build commands and settings used by CodeBuild to run the build
* buildspec.yml can be overwrite by adding own commands in the console when launch the build
* Build logs are in CodeBuild console and Full CodeBuild logs in CloudWatch

