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
- DB encryption must be done at creation time, but also make sure the underlying db instance supports encryption
- S3 static content website hosting can ebe enabled by choosing "Static website hosting" then selecting a bucket to host your website
- Alias records provide Route 53 specific extension to the DNS functionality. An alias contains a pointer to a Cloudfront dist, EBS env, ELB, ALB, CLB or S3 bucket.
- AWS Storage Gateway-cached volumes let you use S3 as your primary data storage while retaining frequent data in your storage gateway.
- Elastic Beanstalk can be used to host Docker containers. 
- SQS helps facilitate horizontal scaling of encoding tasks
- Difference between AWS Direct Connect and VPC VPN is that the latter goes over the internet using IPSec via encrypted network connectivity
- AWS Lambda automatically reports metrics through AWS Cloudwatch on your behalf through Cloudwatch Logs
- Cloudfront can use signed URLs or signed cookies via date, time, ip or range of ip's.
- Origin Access Identity users enforce using Cloudfront URLs instead of the S3 bucket. Setup custom origin headers in S3 to prevent access. 
- In order for S3 buckets to 'serve content', Cross-Origin Resource Sharing must be configured
- When launching an EC2 instance, you can pass user data that performs common automated configuration tasks and run scripts after the instance starts
- VM Import/Export enables customers to import VM images in order to create EC2 instances. 
- AWS Fargate allows you to run your containerized apps without the need to provision and manage the backend infrastructure. 
- A public IP address of an EC2 instance is released after an instance is stopped/started. 
- AWS PrivateLink provides a secure private connectivity between separate VPCs whereas VPC peering is not secure. 
- Redshift never deletes manual snapshots automatically like it does for automatic snapshots ( 1-35 days max )
- EMR is a managed cluster platform for running big data frameworks, processing a mass amt of data in/out of aws data stores/databases
- Cloudwatch Metrics help you monitor the physical aspects of a Redshift cluster. 
- Cloudfront query string forward only supports Web Distribution. The delimiter must always be an & character. Params are case sensitive.
- Weighted Routing Policy is the ideal approach for Blue-Green deployments
- Throughput Optimized (st1) is good for Max Throughputh Volume of 500 MiB/s in batch processing activities
- Amazon Elastic Container Registry (ECR) is a fully-managed Docker container registry for storing, managing and deploying docker container images
- Tags on instances with segregated access via IAM policies will allow managing relevant accesses
- DB Sharding allows you to break up a DB into smaller pieces ( Tables) in order to equally split up requests over more instances


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

## Tutorial Dojo exam #1

- With EBS-backed EC2 instances, when shut down, data is unavailable until the instance is restarted
- Understand CIDR 
- Redshift Spectrum lets a data analyst conduct fast, complex analysis on objects stored on the AWS cloud
- DynamoDB partition Keys?
- IAM Databse Authentication works with MySQL and Postgres, no password needed to connect to a DB instance, instead a token auth
- AWS Budgets sets alerts for costs or usage exceeded
- Client side encryption is the act of encrypting data before sending it to AWS S3.
- To enable Client-side encryption, use AWS KMS-managed customer master key and use a client side master key
- No additional charge for Cloudformation
- You can also install CloudWatch Agent to collect more system-level metrics from Amazon EC2 instances like Memory utilization
- When you create or update Lambda functions that use environment variables, AWS Lambda encrypts them using the AWS Key Management Service.
- 1. Subtract 32 with the mask number : (32 - 27) = 5
- 2. Raise the number 2 to the power of the answer in Step #1 : 2^ 5 = (2 * 2 * 2 * 2 * 2) = 32
- Amazon DynamoDB Accelerator (DAX) is a fully managed, highly available, in-memory cache that can reduce response times from milliseconds to microseconds.
- You can join multiple gp2, io1, st1, or sc1 volumes together in a RAID 0 configuration to use the available bandwidth.
- AWS Directory Service provides multiple ways to use Amazon Cloud Directory and Microsoft Active Directory (AD) with other AWS services
- When you create or modify your DB instance to run as a Multi-AZ deployment, Amazon RDS automatically provisions and maintains a synchronous standby replica in a different Availability Zone
- AWS RDS Enhanced Monitoring metrics are stored in the CloudWatch Logs for 30 days by default. 
- You can access the OS of AWS EMR (Hadoop framework) EC2 instances. 
- [SAML Auth](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_saml.html)
