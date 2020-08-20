## S3 Summary

- S3 is **object-based** - allows you to upload files.
- Files can be 0 - 5TB.
- Unlimited storage.
- Files stored in buckets.
- S3 is a universal namespace (names must be globally unique).
- Read after Write consistency for PUTs of new objects.
- Eventual Consistency for overwrite PUTs and DELETEs (can take some time).

#### Storage classes/tiers
- S3 - durable, immediately available, frequently accessed.
- S3 IA - durable, immediately available, infrequently accessed.
- S3 One Zone IA - same as IA but data is store in a single availability zone.
- S3 Reduced Redundancy Storage - data that is easily reproducible.
- Glacier - archived data that takes 3 - 5 hours to access.

#### S3 objects
- Key (name)
- Value (data)
- Version ID
- Metadata
- Subresources
  - Bucket policies, ACLs
  - CORS
  - Transfer acceleration

#### S3 security
- By default, all S3 buckets are PRIVATE.
- You can set up access using:
  - Bucket policies (bucket level)
  - Access control list (object level)
- S3 buckets can be configured to create access logs that log all requests made to the S3 bucket. These logs can be written to another bucket.

#### S3 encryption
- Encryption In-Transit
 - SSL/TLS
- Encryption At Rest
 - SSE-S3 (AES-256 bit)
 - SSE-KMS
 - SSE-C (customer provided key)
- Client Side Encryption

We can create a bucket policy to prevent unencrypted files from being uploaded by creating a policy that only allows requests that include the **x-amz-server-side-encryption** parameter in the request header.

#### S3 CORS (cross origin resource sharing)
- Used to enable cross origin access for AWS resources (e.g. S3 hosted website accessing javascript or image files in another bucket).
- By default, resources in one bucket cannot access resources in another bucket.
- Always use the S3 website URL, not the regular bucket URL.
S3 URL: http://<bucket_name>.s3-website.<region>.amazonaws.com

#### S3 CloudFront
**Edge Location** - Location where content will be cached (note this is NOT a region/AZ)
  - These are READ and WRITE.
  - Objects are cached for the TTL.
  - You can clear objects using invalidation, but fees apply.
**Origin** - This is the origin of all the files the CDN will distribute. These can be an S3 bucket, an EC2 instance, an ELB or Route53.
**Distribution** - Name given to the CDN, which consists of a collection of edge locations.
