# Domain 4: Design Cost-Optimized Architectures

## 4.1 Determine how to design cost-optimized storage.

Pricing Overview
- Pay as you go
- Pay less when you reserve
- Pay even less per unit by using more

S3 Pricing Considerations
- Storage Class
- Storage 
- Requests
- Data Transfer

EBS Pricing Considerations
- Volumes ( How many you provision )
- Input/output IOPS ( operations per second )
- Snapshots
- Data Transfer

## 4.2 Determine how to design cost-optimized compute.

In Reserved Instances, you can use instance flexbility when using Linux and Region. 
- You will be charged at half the normal on-demand price if using a bigger instance
- No instance flexibility with Windows, you pay normal on-demand pricing

EC2 Cost Pricing
- Reserved Instances (75% cheaper compared to on-demand pricing)
  - Standard RIs
  - Convertible RIs: Converted to other EC2 Instance types
  - Scheduled RIs : Few hours every weekend
  
- Spot Instances ( 30-45% cheaper than on-demand prices )
  - Spot market price which is dynamic
  - Lose your instance if your price goes above your bid
  - You can hibernate your instance which puts your instance to sleep if it goes above spot price
  - Spot Blocks: Reserve a block of time, up to 6 hours on the spot market
  
Cloudfront
- Reduces cost by caching it on Cloudfront
- No data charge by moving data from S3 to Cloudfront
- Cost is based on how widely you want to distribute the content ( globally vs specific regions )
  - Traffic distribution
  - Requests
  - Data transfer out
