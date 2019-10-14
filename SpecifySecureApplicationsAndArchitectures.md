# Domain 3: Specify Secure Applications and Architectures

## 3.1 Determine how to secure application tiers.

- Security:
  - Security Groups - Operate at the instance or Network Interface level
  - Access Control Lists - Operate at the subnet level
  - Main diff between two is only Security Groups let you allow traffic
  - Access Control Lists let you allow and deny
  - Use security groups to control traffic "into, out of, and between resources"
  - Security Groups are sufficient to allow an instance to access another tier
  - Security Groups can span multiple Availability Zones
  
- Customers are responsible for:
  - platform, applications, IAM, OS, Network, Firewall, Client side encryption, server side data encryption and network traffic protection
- IAM
  - Roles: Temporary identies used by EC2, Lambdas and external users
  - Federation: users with active directory
  - Web Identity Federation: Users with web identities from Amazon.com  or other Open ID provider using Secure Token Service (STS)

Network Traffic
- A security group can grant access to traffic from the allowed networks via the CIDR range for each
network. 
- VPC peering and VPN are connectivity services and cannot control traffic for security
- NAT Gateways must be deployed in public subnets

Bucket Policies
- Explicit "Deny" will always trump all other permissions

CloudTrail
- Very important for security
- Enabled by default on new accounts
- Auditing tool

## 3.2 Determine how to secure data.

Data in Transit
- Create an Origin Access Identity (OAI) for CloudFront and grant access to the objects in your S3 bucket to that OAI.
- SSL over web
- VPN for IPsec
- IPsec over AWS Direct Connect
- Import/Export/Snowball

Data at Rest
- S3 data private by default
- SSE-KMS, SSE-S3, SSE-C ( Server side and more performant )
- CSE-KMS, CSE-C ( Client side for compliance/regulation but less performant )

Managing your Keys
- Key Management Service ( Customer software-based key mgmt, integrated with many AWS services directly )
- AWS CloudHSM ( FIPS 140-2 compliance, hardware based key mgmt, use directly from application )

Network isolation:
- Internet Gateways: Connect to the internet
- Virtual Private Gateways: Connect to VPN
- AWS Direct Connect: Dedicated pipe
- VPC peering: Connect to other VPC's
- NAT Gateways: Allow internet traffic from private subnets
- Prefer IAM Roles to access key
 
- VPC endpoints for Amazon S3 provide secure connections to S3 buckets that do not require a
gateway or NAT instances. 
- NAT Gateways and Internet Gateways still route traffic over the Internet to the
public endpoint for Amazon S3. 
- There is no way to connect to Amazon S3 via VPN

## 3.3 Define the networking infrastructure for a single VPC application

Private subnets:
- Outbound-only access: NAT/proxy/bastion host
- Not accessible from the public internet
- Do not have a routing table entry to an internet gateway
- Elastic IPs are sticky until re-assigned for a good reason (such as the instance has been terminated i.e. it is never coming back).

Direct Connect
- Directly connects your data center to AWS
- Useful for high throughput workloads ( lots of network traffic )
- Or if you need a stable and reliable secure connection
- Good solution if you're using a VPN connection and it keeps dropping out. 

VPC Endpoints
- Two types
  - Interface Endpoints
  - Gateway Endpoints ( Currently supports S3 and DynamoDB )
- Privately connect your VPC to supported AWS services and VPC endpoint services powered by PrivateLink
- Does not require an internet gateway, NAT device, VPN connection or AWS Direct Connect connection
- Instances do not require public IP addresses to communicate with resources in the service
- Traffic does not leave the Amazon network
- Endpoints are virtual, horizontally scalled, redundant and hilghly available VPC components 
- They do not impose availability risks or bandwidth constraints on your network traffic

Route 53
- You cannot define paths like "/news" for records  
