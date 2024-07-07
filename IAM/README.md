# Table of Contents
1. [What is IAM](#What-is-IAM)
2. [What is IAM User](#Amazon-is-iam-user)
3. [What are IAM Policies](#what-are-iam-policies)
4. [What are IAM Policies Type](#what-are-iam-policies-type)
5. [What are IAM Roles](#what-are-iam-roles)

## What is IAM

AWS Identity and Access Management (IAM) is a web service that helps you securely control and access to AWS resources.

## What are the feature of IAM

Shared access to your AWS account
    without providing your credentials, allow other persons to manage the resources
Granular permissions
    You can grant different permissions to different people for different resources.
Secure access to AWS resources for applications that run on Amazon EC2
    Grant the access to the application to use other aws resources on your behalf
Multi-factor authentication (MFA)
    Use MFA to secure your account

## What is IAM User

IAM users are the users for humen to access the AWS resources with assigned permissions/policies

## What are IAM Policies
When a IAM user try to loggin, it will not be able to access the resources. We have to give permissions to that user. To give permissions we use policies, which is json document in which we define which user will be given to which permissions of which resources.

### Elements of JSON Policy Document

1- Version
2- Statement
    - SID
    - Effect
    - Principal
        - Service
    - Action
    - Resource
    - Condition Block

#### Version

Specify the version of the policy language that you want to use. It is recomended to use the version 2012-10-17.

#### Statement
Use this main policy element as the container for the following elements

##### SID 
Include optional statement ID to differentiate between your statements

##### Effetct
Use Allow/Deny to indicate whatever the policy will allows or denies.

##### Principal

Required only in some circumstances

    1- If you create a resource-based policy, you must indicate the account, user, role, or federated user to which you would like to allow or deny access. 

    1- If you are creating an IAM permission policy to attach to a user or role, you cannot include this element.

"Principal": {
    "AWS":["arn:aws:iam::account-id:root"]
    }

##### Action

Include the list of actions that the policy allows or denies.
e.g
s3:GetObject,
s3:PutObject


##### Resource

Required only in some circumstances

1- If you are creating an IAM permissions policy, you must specify a list of resources to which the action apply.
2- If you create a resource-based policy, this element is optional. 

"Resource": ["arn:aws:s3:::mybucket/*"]

##### Condition (optional)
Specify the circumestances under which the policy grants permissions

Examples:
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "SID": "1",
            "Effect": "Allow",
            "Principal": {
                "AWS": ["arn:aws:iam::account-id:munawar"]
            },
            "Action": [
                "s3:GetObject",
                "s3:PutObject"
            ],
            "Resource": ["arn:aws:s3:::mybucket/*"]
        }
    ]
}
```


Summery:

"munawar" can perform GetObject and PutObject action on mybucket resource

## What are IAM Policies Type

1. Identity-based policies
2. Resource-based policies

### Identity-based policies
Identity-based policies are permissions policies that you attach to an IAM identity, such as an IAM user, group, or role.
Identity-based policies control what actions the identity can perform, on which resources, and under what conditions.

1. Managed policies 
2. Inline policies

### Resource-based policies
Resource-based policies are permissions policies that you attach to a resource such as an Amazon S3 bucket ( my_bucket )

Note:

If a user attached identity-based policy and in that policy user is not allowd to perform the action on resource but there is a policy on resource in which it is defined that any user can access this resource then user can access that resource.

## How to attach the policies
Following are different ways to attach the policies

3. Policies and Accounts
2. Policies and Users
1. Policies and Groups



## Terms in AWS

### AWS Service

High level services like ec2, s3, lambda, 

### AWS Resource

Resource is basically comes under the aws service. For instance, s3 is a aws service. my_bucket is a resource in s3. A resource is an entity that you can work with


## What are IAM Roles

An IAM role is an IAM identity that you can create in your account that has specific permissions.

1. A role does not have standard long-term credentials just like iam user
2. A role can be assumbled to anyone who needs it
3. With a role we can assign delegate access to users, applications and services.