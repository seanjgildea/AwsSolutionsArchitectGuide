# 2019 AWS Solutions Architect Associate Exam Guide


- [Domain 1 Design Resilient Architectures](DesignResilientArchitectures.md) 34%

- [Domain 2 Define Performant Architectures](DefinePerformantArchitectures.md) 24% 

- [Domain 3 Specify Secure Applications and Architectures](SpecifySecureApplicationsAndArchitectures.md) 26% 

- [Domain 4 Design Cost-Optimized Architectures](DesignCostOptimizedArchitectures.md) 10% 

- [Domain 5 Define Operationally Excellent Architectures](DefineOperationallyExcellentArchitectures.md) 6%


## Mock Exams

- [Mock Exam 1](https://d1.awsstatic.com/training-and-certification/docs/AWS_Certified_Solutions_Architect_Associate_Sample_Questions.pdf)


## Areas to focus on:

- Route 53 Routing options
- S3 to Cloudfront
- Origin Identity Access variations
- ELBs
- ALBs
- Classic Load Balancers
- VPC options for private networks
- Lifecycle policies for S3 Buckets. You specify lifecycle management of objects in an S3 bucket. The configuration is a set of one or more rules where each rule defines an action for S3 to apply to a group of objects. These can be transition actions: "When objects transition from one storage class to another" or Expiration actions: specify when objects expire. 
- Hexadecimal hash for S3 Object prefixes greatly increase performance
- VPC Flog logs catpure IP traffic going to and from network interfaces in your VPC. It's stored in CloudWatch logs. 
- Glacier Expedited: 1-5 minutes for archives < 250gb
- Glacier Standard: 3-5 hours
- Glacier Bulk: 5-12 hours
- EBS Volume snapshots to S3 are incremental, which means that only the blocks on the device that have changed afte ryour most recent snapshot are saved. 
- IAM roles for ECS tasks lets you specify an IAM role that can be used by the containers in a task. 
- Lifecycle Hooks in Auto Scaling Groups let you put an instance into a 'wait state' before termination so you can perform custom activities and retrieve critical operational data from a stateful instance. 
- S3 event notification can invoke lambda functions for file processing
- Aurora clusters can grow up to 64 TB in size and replica lag is less than 100 ms after primary instance has written an update
- EBS can provision worker processes
- KMS master keys are region specific 
- KMS will rotate keys annually and use the appropriate keys to perform cryptographic operations
- Minimum size of EBS: Throughput Optimized HDD is 500GB
- Bastion hosts should be deployed in public subnets
- Redshift Enhanced VPC Routing provides VPC resources access to Redshift. Redshift requires this to access S3 resources. 
- VPC Endpoints allow you to connect your VPC to AWS resources without requiring a NAT instance
- Provisioned IOPS SSD is for operations requiring more than 16,000 IOPS or 250 MiB/s of throughput per volume
- For Redshift, you can enable Cross-Region Snapshots to another region 
- For EBS Volumes, you create a snapshot and copy it to a new region
- Cloudtrail monitors API calls and sends logs to an S3 bucket
- Cognito Identity can also support OIDC, SAML and it's own identity pools
- Cloudfront access logs and capturing requests sent to the Cloudfront API

## VPC Notes

- Gateway VPC Endpoint provides secure private access to S3 and DynamoDB without using the internet.
- AWS PrivateLink provides secure private access to AWS services by adding an ENI within a VPC
- Use Multi-AZ to ensure high availability for an RDS service rather than read replicas
- S3 Pre-signed URL's are the perfect solution when you want to give temporary access to users for S3 buckets
- Route 53 Multivalue answer routing is perfect for responding to DNS queries of up to 8 healthy records at random
- If you need the IPv4 address of your end user, look for the X-Forwarded-For header.
- Use ALB's if you want to do intelligent routing
- Use Classic ELB's for basic routing 
- Both ALB's and CLB's do not create an Elastic IP at creation, you need to copy the A record into Route 53

- Sticky Sessions: Bind a users session to a specific EC2 instance ( classic load balancer ). This ensures all requests stay with the same instance. You can enable for ALB's but traffic will be sent at the target level. 
- If you have an EC2 instance not receiving any traffic, you want to DISABLE sticky sessions or ENABLE cross-zone load balancing

- No Cross Zone Load Balancing: Cannot send traffic from one overloaded AZ to a lightly loaded EZ elsewhere
- Cross-Zone Load Balancing: Can send traffic across zones to balance evenly
- 
- S3 Signed URL's vs Cloudfront Pre Signed URLs
- Pre-signed URLs include the creators security credentials, bucket name, object key and HTTP method (PUT) and expiration date for a specific duration. 
- Multivalue Routing: Simple Routing but with Health Checks


## Important Topics to know

1. The 30 Day constraint in the S3 Lifecycle Policy before transitioning to S3-IA and S3-One Zone IA storage classes

2. Enabling Cross-region snapshot copy for an AWS KMS-encrypted cluster

3. Redis Auth / Amazon MQ / IAM DB Authentication

4. Know that FTP is using TCP and not UDP (Helpful for questions where you are asked to troubleshoot the network flow)

5. Difference between S3, EBS and EFS

6. Kinesis Sharding

7. Handling SSL Certificates in ELB ( Wildcard certificate vs SNI )

8. Difference between OAI, Signed URL (CloudFront) and Pre-signed URL (S3)

9. Different types of Aurora Endpoints

10. The Default Termination Policy for Auto Scaling Group (Oldest launch configuration vs Instance Protection)

11. VPC/VPN/ELB

12. Route Table vs Security Group

13. Gateways Endpoints vs VPC Endpoints

14. Aurora Endpoints ( Instance, Reader, Cluster )

15. Dynamo Streams: Associate a stream ARN with a lambda function you write. 

16. Sign-in via AWS Cognito User Pool (Third party federation) and sign-in via Cognito Identity Pool (federated identities) are independent of one another.

17. Enhanced VPC Routing

18. Failover Routing Policy:
