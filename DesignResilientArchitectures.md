# Domain 1: Design Resilient Architectures

## 1.1 Choose reliable/resilient storage.

### 3 Options for Storage

- EC2 Instance Store ( Ephemeral storage ) Fixed capacity, app level durability ( caching, storing data )

- EBS Elastic Block Store 
  - Connects to one EC2 Instance at a time 
  - Decoupled from the EC2 Instance unlike Ephemeral storage
  - Provisioned Capacity
  - Multiple volumes 
  - Raid Zero and Striping to achieve 
  
- 4 Types of EBS Volumes
  - General Purpose SSD (gp2)
  - Provisioned IOPS SSD (io1)
  - Throughput Optimized HDD (st1)
  - Cold HDD (sc1)

- EFS Elastic File System
  - Petabyte scale file system
  - Linux based AMI's
  - Shared storage
  
- Object Storage 

  - S3 is the primary option 
  - S3 is a distributed system
  - S3 gives you strong consistency for new objects
  - S3 gives you eventual consistency for existing objects
  - Many storage classes and Durability

## 1.2 Determine how to design decoupling mechanisms using AWS services.

- If one component fails, the other does not

## 1.3 Determine how to design a multi-tier architecture solution.

- Each tier can scale independently

## 1.4 Determine how to design high availability and/or fault tolerant architectures.

- Operate at scale. Stay highly operational 
