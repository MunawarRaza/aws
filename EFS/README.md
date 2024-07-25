# Table of Contents
1. [What is EBS](#What-is-EBS)
2. [What are EBS Features](#what-are-ebs-features)

## What is EBS

Amazon Elastic Block Store (Amazon EBS) provides scalable, high-performance block storage resources that can be used with Amazon Elastic Compute Cloud (Amazon EC2) instances. it is network device not physical device.

### Some Points about EBS

- These are netowkr devices not pyhical devices. That is why these use the netwokr to communicate the instance which means there might be a bit of latency
- They can only be mount to one EC2 at a time. These can be detached and attached to anyother EC2 quickly
- They are bound to specific AZ
    - An EBS Volume in us-east-1a cannot be attached to us-east-1b
    - To move a volume across, you first need to snapshot it
- Data is persistent, even after the termination of EC2
- Following actions can be performed with volume
    - Create volume
    - Delete volume
    - Attach and Detach 
    - Modify ( Size, IOPS, Throughput)
    - Create Snapshots
    


## What are EBS Features
1. Multiple volume types
2. Scalability
3. Backup and recovery
4. Data protection
5. Data availability and durability
6. Data archiving

### Volume Disk type

There are two major types of EBS volume
1. SSD-backed storage for transactional workloads
2. HDD-backed storage for throughput intensive workloads

### Volume type
1. General Purpose SSD ( gp2, gp3 )
2. Provisioned IOPS SSD ( io1, io2 )
3. Throughput Optimized HDD ( st1 )
4. Cold HDD
5. Magnetic

- #### General Purpose SSD ( gp2, gp3 )
    - General Purpose SSD (gp2 and gp3) volumes offer cost-effective storage that is ideal for a broad range of workloads

- #### Provisioned IOPS SSD ( io1, io2 )

    - Provisioned IOPS SSD (io1 and io2) volumes provide low latency and are designed to meet the needs of I/O-intensive workloads. They are best for EBS-optimized instances.

- #### Throughput Optimized HDD ( st1 )

    - Throughput Optimized HDD (st1) volumes provide low-cost magnetic storage that is a good fit for large, sequential workloads.

- #### Cold HDD
    - Cold HDD (sc1) volumes provide low-cost magnetic storage that offers lower throughput than st1. sc1 is a good fit for large, sequential cold-data workloads that require infrequent access to data.

- #### Magnetic
    - Magnetic (standard) volumes are best suited for workloads where data is accessed infrequently.

### Scalability
As your needs changes, you can use Elastic Volumes operations to dynamically increase capacity or tune performance, with no downtime

### Backup and recovery

You can use Amazon EBS snapshots to back up the data stored on your volumes.You can then use those snapshots to instantly restore volumes or to migrate data across AWS accounts, AWS Regions, or Availability Zones

### Data protection
Use Amazon EBS encryption to encrypt your Amazon EBS volumes and Amazon EBS snapshots.

### Data availability and durability

io2 Block Express volumes provide 99.999% durability with an annual failure rate of 0.001%. Other volume types provide 99.8% to 99.9% durability with an annual failure rate of 0.1% to 0.2%.

### Data archiving
EBS Snapshots Archive provides a low-cost storage tier to archive full, point-in-time copies of EBS Snapshots that you must retain for 90 days or more for regulatory and compliance reasons, or for future project releases.

## Cloud storages

1. Block Storage
2. Object Storage
3. File Storage

### Block Storage
Block storage offers high-speed data processing, low latency, and high-performance storage. Any service that requires fast access to data works well with block storage
For example, real-time analytics, high-performance computing, and systems with many rapid transactions all benefit from block storage.

Block storage works by dividing data into equal size of chunks, which are called blocks. The operating system gives each block a unique address or block number or index, which are logged inside a data lookup table. The addressing uses a logical block addressing (LBA) scheme that assigns a sequential number to each block.

Block storage allows direct access to individual data blocks. You can read or write data to specific blocks without having to retrieve or modify the entire dataset the block belongs to.

These are accessible via FC/ISCSI

### Object Storage
Object storage stores and manages data as discrete units called objects. An object typically consists of the 
- actual data — such as documents, images, or data values
- its associated metadata — such as date of creation, date of modification, object name etc.
   - Metadata is additional information about the object that you can use to retrieve it. The metadata can include attributes like the unique identifier, object's name, size, creation date, and custom-defined tags.

Object storage is best used for large amounts of unstructured data. Modern organizations create and analyze large volumes of unstructured data such as photos, videos, email, web pages, sensor data, and audio files

These are accessible via NFS or SMB

### File Storage
Cloud file storage is a hierarchical storage system that provides shared access to file data

Cloud file storage is best when users need concurrent access to a shared system of files. Additionally, file-level access control allows you to set up permissions and access control lists (ACLs) to increase security. For example, collaborative work environments that require sharing files between remote teams use file storage

These are accessible via RESTful protocol

## Terms in Storage
1. IOPS
2. Throughput
3. Latency

### IOPS

How many time (read, write) operations are performed on disk in a second. E.g How many time read the data and how many time write the data in a second

### Throughput

How much data MBs is accessed in a second

### Latency

The ammount of time taken between a request and response. 

## What is snapshot
You can back up the data on your Amazon EBS volumes by making point-in-time copies, known as Amazon EBS snapshots. A snapshot is an incremental backup, which means that we save only the blocks on the device that have changed since your most recent snapshot.

- Following Action can be performed with snapshot
    - Create Snapshot
    - Create image from snapshot
    - Create volume from snapshot
    - Copy snapshot from one AZ to another AZ
    - Delete Snapshot
    - Archive snapshot
    - Snapshot Settings ( modify permissions, snapshot lock etc)
