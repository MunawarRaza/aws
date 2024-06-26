# Table of Contents
1. [What is ECR](#What-is-ECR)
2. [What are the components of ECR](#What-are-the-components-of-Amazon-ECR)
3. [How to Authenticate the ECR](#how-to-authenticate-with-ecr)
4. [How to push image to ECR repository](#how-to-push-image-to-ecr-repository)
## What is ECR
Amazon Elastic Container Registry (Amazon ECR) is an AWS managed container image registry service that is secure, scalable, and reliable

## What are the Components of Amazon ECR
Amazon ECR contains the following components:

### Registry

AWS ECR is the private registory which is provided to each AWS account. In this private registry you can create one or more public or private repositories on your need.

### Authorization token

Before push or pull the image, you must have to authenticate your self to ECR as an IAM users. In short, you must have to login before push or pull the images.

### Repository

An AWS ECR registory contains the docker images.

### Repository policy

You can control access to your repositories and the contents within them with repository policies.

### Images
These are the docker images, within the Registory.

## How to Authenticate with ECR
Before push and pull the images, you must have to login into ECR registory. There are multiple methods to authenticate your self.

1. [Using the Amazon ECR credential helper](#Using-the-Amazon-ECR-credential-helper)
2. [Using an authorization token](#Using-an-authorization-token)


### Using the Amazon ECR credential helper
Amazon ECR provides a Docker credential helper which makes it easier to store and use Docker credentials when pushing and pulling images to Amazon ECR. Install the amazon-credentials-ecr-helper packages

```
apt install amazon-ecr-credential-helper
```
### Using an authorization token
Authorization token is used to access the any Amazon ECR registory and is valid for 12 hours. You can get the authorization token using ```aws ecr get-login-password``` command

## How to push image to ECR repository

1. Install AWS cli
2. Configure aws cli
3. Login to ECR
4. Tag the image
5. Push the image

#### Install awscli
```
apt install awscli
```
#### Configure AWS CLI using below command
```
aws configure
```
#### Login to ECR Registory
```
aws ecr get-login-password --region region | docker login --username AWS --password-stdin aws_account_id.dkr.ecr.region.amazonaws.com
e.g
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 590183784162.dkr.ecr.us-east-1.amazonaws.com
```

##### Tag the image

```
docker tag simple-nodejs-app:latest 590183784162.dkr.ecr.us-east-1.amazonaws.com/simple-nodejs-app:latest
```
#### Push the image

```
docker push 590183784162.dkr.ecr.us-east-1.amazonaws.com/simple-nodejs-app:latest
```