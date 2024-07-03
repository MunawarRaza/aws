# Table of Contents
1. [What is IAM](#What-is-IAM)
2. [What is IAM User](#Amazon-is-iam-user)
3. [What are IAM Policies](#what-are-iam-policies)
4. [What are IAM Policies Type](#what-are-iam-policies-type)
5. [What are IAM Roles](#what-are-iam-roles)

## What is IAM

AWS Identity and Access Management (IAM) is a web service that helps you securely control and access to AWS resources.

## What is IAM User

IAM users are the users for humen to access the AWS resources with assigned permissions/policies

## What are IAM Policies

Policies are the permissions and written in JSON document

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

1- Identity-based policies

2- Resource-based policies

### Identity-based policies
Identity-based policies are JSON permissions policy documents that control what actions an identity (users, groups of users, and roles) can perform, on which resources, and under what conditions

1- Managed policies 
2- Inline policies
