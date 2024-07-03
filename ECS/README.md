# Table of Contents
1. [What is ECS](#What-is-ECS)
2. [Amazon ECS terminology and components](#Amazon-ECS-terminology-and-components)
3. [Application Lifecyle](#application-lifecycle)

## What is ECS
Amazon Elastic Container Service (Amazon ECS) is a fully managed container orchestration service that helps you easily deploy, manage, and scale containerized applications.

## Amazon ECS terminology and components
There are three layers in Amazon ECS:

### Capacity
The infrastructure where your containers run
e.g
1. AWS EC2 instance
    
    You choose the instance type, the number of instances, and manage the capacity.

2. AWS Fargate

    Fargate is a serverless, pay-as-you-go compute engine. With Fargate you don't need to manage servers, handle capacity planning, or isolate container workloads for security.

3. On-premisis compute

    Amazon ECS Anywhere provides support for registering an external instance such as an on-premises server

### Controller
Deploy and manage your applications that run on the containers


### Provisioning
The tools that you can use to interface with the scheduler to deploy and manage your applications and containers
e.g
1. AWS CLI
2. Copilot
3. Management Console
4. Terraform
5. Cloud formation

## Application Lifecyle
1. Push image to ECR
2. Define Task definition
3. Deploy application as task or service
4. Capacity

    EC2

    Fargate

    On-Prem

### Push image to ECR
Create docker image using Dockerfile and push the image to ECR

### Define Task definition
After you create and store your image, you create an Amazon ECS task definition. A task definition is a blueprint for your application. It is a text file in JSON format that describes the parameters and one or more containers that form your application. For example, you can use it to specify the image and parameters for the operating system, which containers to use, which ports to open for your application, and what data volumes to use with the containers in the task. The specific parameters available for your task definition depend on the needs of your specific application.

### Deploy application as task or service
After you define your task definition, you deploy it as either a service or a task on your cluster



### Create Cluster

Create Cluster

    Fargate
    EC2
        Infrastructure
            ASG
            Provisioning Model
                On-demand
                Spot
            AMI
            EC2 Instance Type
            EC2 instance Role
            Desired Capacity
                min
                max
            EBS volume
        Networking
            VPC
            Subnets
            Security Groups
            Auto Assign IP
        
### Create task definition

Create task definition

    Task definition configuration
        name
    Infrastructure Requirements
        Launch Type
            AWS Fargate
            AWS EC2
        OS, Architecture, Network mode
        Task Size
            CPU
            Memory
        Task Role
        Task Execution Role
        Task Placement
    Container-1
        Container details
            name
            image url
            Essential container
        Private Registory (when you have a container image in a private registry outside of Amazon ECR)
        Port mappings ( allows a container to access ports on the host to send or receive traffic)
            Container port
            Protocol
            port name
            app protocol
        Resource allocation limits (You can define memory and CPU for your containers )
            CPU
            GPU
            RAM
                min
                max
        Environment variables ( you can add variables that are injected into a container )
    Storage
        Ephemeral
        Add Volume
        Mount Volume from container



Note: 

Task Role:

    It is used by the containers.
    Allow containers to make the API calls to AWS services on your behalf.
    e.g

    - When application calls to S3 bucket, this IAM role will be used
    - When application has to call to lambda function, this IAM role will be used
    - When application has to call SES/SNS service, this IAM role will be used

Task execution role:

    It is used by the ECS tasks.
    e.g
    - To pull the image from ECR
    - To Send the logs to Cloudwatch
    - To authenticate with private ECR registry
    - 
