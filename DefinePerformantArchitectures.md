# Domain 2: Define Performant Architectures

## 2.1 Choose performant storage and databases.

Performant Storage
- EBS Volumes mounted as discs 
- SSD vs HDD ( random access vs sequential access )
- Offload all static content to S3 instead of keeping it on EC2 servers which dramatically improves your webserver performance for serving dynamic content
- buckets are tied to a region
- S3 payment model: GB's per month, transfer out of region, PUT/COPY/POST/LIST/GET requests
- S3 free of charge: transfer in
- S3 Lifecycle Policies move cold older data to Glacier cheaper storage

Performant Databases
- RDS
  - med/high read/write
  - use read replicas to increase performance and take load off the master db
- DynamoDB
  - You dont specify the data footprint you need, it grows as you
  - However you DO specify throughput, how many reads and writes per second you want
  - Scales the table to handle that throughput
  - Massive read/write rates
  - Limitless storage
  - unlimited horizontal scalability by adding more servers
  - RCU ( Read Capacity Unit ) for up to 4KB in size
  - WCU ( Write Capacity Unit ) for up to 1KB in size
- Redshift
  - Relational DB

## 2.2 Apply caching to improve performance.

- Cache using Cloudfront ( CDN )
  - If the edge location does not have the data it is fetched from the origin location 
- Elasticache
  - Used with databases to take some load off your databases
  - Memcached ( easy to setup, horizontal scalability, low maintenance, multithreading )
  - Redis ( complex ) 
  - Elasticache sets them up for you

## 2.3 Design solutions for elasticity and scalability.

- 
