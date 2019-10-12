# Domain 2: Define Performant Architectures

## 2.1 Choose performant storage and databases.

- EBS Volumes mounted as discs 
- SSD vs HDD ( random access vs sequential access )
- Offload all static content to S3 instead of keeping it on EC2 servers which dramatically improves your webserver performance for serving dynamic content
- buckets are tied to a region
- S3 payment model: GB's per month, transfer out of region, PUT/COPY/POST/LIST/GET requests
- S3 free of charge: transfer in
- S3 Lifecycle Policies move cold older data to Glacier cheaper storage

## 2.2 Apply caching to improve performance.

## 2.3 Design solutions for elasticity and scalability.
