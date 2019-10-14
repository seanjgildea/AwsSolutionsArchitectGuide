# Domain 1: Design Resilient Architectures

## 1.1 Choose reliable/resilient storage.

3 Options for Storage

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

  - S3 Standard, 99.99% availability, 11 9's durability
  - S3- IA ( Infrequently Accessed ) Lower fee than S3 but charged retrieval fee
  - S3 One Zone - IA , do not require multiple availability zone data resilience -
  - S3 - Intelligent Tiering - 99.9% availability ( Moves stale data to lower tiers automatically )
  - S3 Glacier - Data archive
  - S3 Glacier Deep Archive - retrieval time of 12 hrs is acceptable ( Lowest cost! )
  - S3 gives you strong consistency for new objects
  - S3 gives you eventual consistency for existing objects
  - Many storage classes and 99.999999999 Durability
  - Glacier ( bulk 12 hrs, expedited 5 minutes ) encrypts data by default , regional durability
  - EBS, S3 and EFS allow native encryption of data at rest
  - S3 bucket names are global
  - To prevent accidental data loss with S3, enable versioning and MFA Delete on bucket
  
- Encryption At Rest (Server Side) is achieved by:
  - S3 Managed Keys - SSE - S3
  - AWS Key Management Service, Managed Keys - SSE-KMS ( cooperative encryption )
  - Server Side Encryption with Customer provided Keys - SSE-C

## 1.2 Determine how to design decoupling mechanisms using AWS services.

- Use SQS to queue work asynchronously even when resources are offline 
- Use SQS with a load balancer when distributing a heavy load to instances
- Use Elastic IP addresses to route clients to a new server identity when one goes offline

## 1.3 Determine how to design a multi-tier architecture solution.

- Each tier can scale independently

## 1.4 Determine how to design high availability and/or fault tolerant architectures.

- 
