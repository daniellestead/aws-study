## S3 Security

#### Securing buckets
Bye default, all new buckets are PRIVATE. You can set up access to bucket using
either bucket policies (applied at bucket level) or access control lists
(applied at object level). Buckets can be configured to create access logs,
which can be written to another bucket.

## S3 Policies

#### Creating a bucket
1. Go to create bucket and enter a DNS compliant bucket name. If the bucket name
already exists you will be notified.
2. All bucket properties are disabled by default, but we add a key-value tag in
this lab.
3. Create bucket.

#### Bucket policies
1. Go to Permissions > Bucket Policy. Policies are written in json, but there is
a convenient policy builder.

## Encryption

#### Types of encryption
* In Transit
  - Encrypting the data being sent to and from S3 (SSL/TLS)

* At Rest
  - Server side encryption
      - S3 Managed Keys **SSE-S3**
      - AWS Key Management Service **S3-KMS**
      - Server Side Encryptions with customer provided keys **SSE-C**
  - Client side encryption
      - You encrypt files before upload them to S3

#### Enforcing encryption
Every time a file is uploaded, a PUT request is initiated. Inside this PUT
request is 'Expect: 100-continue'. If the file is to be encrypted at upload
time, the **x-amz-server-side-encryption** parameter will be in the PUT request
header.

There are two options available:
- x-amz-server-side-encryption: AES256
- x-amz-server-side-encryption: ams:kms

You can enforce use of encryption by using a bucket policy that denies any S3
PUT request that doesn't include the encryption parameter in the header.

To do this, we need to create a DENY policy with the PutObject action and a
condition with 'StringNotEquals', key = 's3:x-amz-server-side-encryption' and
value = 'aws:kms'.

Note: you may need to add the '/*' wildcard to the arn resource name.
