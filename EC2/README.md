# Table of Contents
1. [What is EC2](#What-is-EC2)
2. [What are the feature of EC2](#What-are-the-feature-of-EC2)
3. [What are the related services of EC2](#What-are-the-related-services-of-EC2)
4. [What are Instances Types](#What-are-Instances-Types)
5. [What is the Naming Convention of Instance Type](#What-is-the-Naming-Convention-of-Instance-Type)
6. [When to chose which instance type](#When-to-chose-which-instance-type)
7. [How to Create EC2](#How-to-Create-EC2)
8. [What are the Storage options](#what-are-the-storage-options)

## What is EC2

Amazon Elastic Compute Cloud (Amazon EC2) provides on-demand, scalable computing capacity in the Amazon Web Services (AWS) Cloud. An EC2 instance is a virtual server in the AWS Cloud

EC2 Instance offers different balance of
1. Compute
2. Memory
3. Network
4. Storage

## What are the feature of EC2

1. Instance
2. Amazon Machine Images (AMIs)
3. Instance Type
4. Amazone EBS volume
5. Instance Storage Volume
6. Key Pairs
7. Security Group

#### Instance
Virtual Server

#### AMIs
Preconfigured templates for your instances that package the components you need for your server (including the operating system and additional software).

#### Instance Type
Various configurations of CPU, memory, storage, networking capacity, and graphics hardware for your instances.

#### EBS Volume
Persistent storage volumes for your data using Amazon Elastic Block Store (Amazon EBS).

#### Instance store volumes
Storage volumes for temporary data that is deleted when you stop, hibernate, or terminate your instance.

#### Key Pairs
Secure login information for your instances. AWS stores the public key and you store the private key in a secure place.

#### Security Group
A virtual firewall that allows you to specify the protocols, ports, and source IP ranges that can reach your instances, and the destination IP ranges to which your instances can connect.

## What are the related services of EC2
1. AWS Auto Scalling
2. AWS Backup
3. AWS Cloud Watch
4. AWS ELB
5. AWS GaurdDuty
6. EC2 Image Builder
7. AWS Launch Wizard
8. AWS Systems Manager


## What are Instances Types

When you launch an instance, the instance type that you specify determines the hardware of the host computer used for your instance. Each instance type offers different compute, memory, and storage capabilities, and is grouped in an instance family based on these capabilities

Current Generation of Instance Type:

#### General purpose ( M, T )

M5 | M5a | M5ad | M5d | M5dn | M5n | M5zn | M6a | M6g | M6gd | M6i | M6id | M6idn | M6in | M7a | M7g | M7gd | M7i | M7i-flex | Mac1 | Mac2 | Mac2-m1ultra | Mac2-m2 | Mac2-m2pro | T2 | T3 | T3a | T4g

#### Compute optimized ( C )
C5 | C5a | C5ad | C5d | C5n | C6a | C6g | C6gd | C6gn | C6i | C6id | C6in | C7a | C7g | C7gd | C7gn | C7i | C7i-flex

#### Memory optimized ( R, U, X )
R5 | R5a | R5ad | R5b | R5d | R5dn | R5n | R6a | R6g | R6gd | R6i | R6idn | R6in | R6id | R7a | R7g | R7gd | R7i | R7iz | U-3tb1 | U-6tb1 | U-9tb1 | U-12tb1 | U-18tb1 | U-24tb1 | U7i-12tb | U7in-16tb | U7in-24tb | U7in-32tb | X1 | X2gd | X2idn | X2iedn | X2iezn | X1e | z1d

#### Storage optimized ( D, H, I )
D2 | D3 | D3en | H1 | I3 | I3en | I4g | I4i | Im4gn | Is4gen

#### Accelerated computing ( D, G I, P, Tr )
DL1 | DL2q | F1 | G4ad | G4dn | G5 | G5g | G6 | Gr6 | Inf1 | Inf2 | P2 | P3 | P3dn | P4d | P4de | P5 | Trn1 | Trn1n | VT1

#### High-performance computing ( H )
Hpc6a | Hpc6id | Hpc7a | Hpc7g

## What is the Naming Convention of Instance Type

Instance types are named based on their family, generation, processor family, additional capabilities, and size

c7gn.xlarge

- c --> Instance Family
- 7 --> Instance Generation
- g --> Processor Family
- n --> Additional Capability
- xlarge --> instance size

### Instance Family

- C --> Compute optimized
- G --> Graphic optimized
- I --> Storage optimized
- M --> General purpose
- T --> Burstable performance
- R –-> Memory optimized

### Processor Family

- a --> AMD processor
- g --> AWS Graviton processors
- i --> intel processor

## When to chose which instance type

#### General purpose
Provide a balance of
- compute
- memory
- networking

These instances are ideal for applications that use these resources in equal proportions, such as web servers and code repositories.

#### Compute Optimized
- Batch processing
- Media Transcoding
- High performance web servers
- High Performance computing
- For Machine Learning
- Dedicated gaming servers

#### Memory optimized
- High performance relational/non-relational databases
- In memory database optimized for BI ( Business Inteligence )
- Application performing real time processing of big unstructured data

## How to Create EC2

- Name 
- AMI
- Instance Type
- Key pairs
- Networking
    - VPC
    - Subnet
    - Auto Assign Public IP
    - Security Group
- Storage
    - GP2/GP3/io1/io3/standard
- Advance details

## What are the storages options

Amazon EC2 provides you with flexible, cost effective, and easy-to-use data storage options for your instances. Each option has a unique combination of performance and durability.

### Elastic Block Storage (EBS)
Amazon EBS provides durable, block-level storage volumes that
- you can attach and detach from your instances.
- You can attach multiple EBS volumes to an instance
- You can encrypt your EBS volumes
- To keep a backup copy of your data, you can create snapshots from your EBS volumes
- Snapshots are stored in Amazon S3.
- You can create an EBS volume from a snapshot

### Instance Store

### AWS Elastic File System ( EFS )
- Amazon EFS provides scalable file storage for use with Amazon EC2
- You can create an EFS file system and configure your instances to mount the file system.
- You can attach EFS with multiple instances at a time for common data storage

### Amazon Simple Storage Service (Amazon S3)
- You can use S3 to store and retrive any ammount of data at any time from anywhere over the internet.
- You can use S3 store the backups, logs, files etc.
