## S3 Performance Optimisation

These optimisations are designed for high request rates, such as S3 receiving > 100 PUT/LIST/DELETE requests or >300 GET requests per second.

**GET-Intensive workloads** - Use CloudFront, this will cache objects and reduce latency for GET requests.

**Mixed request workloads** - S3 uses key names to partition objects. The use of sequential key names (timestamps etc) increases the chance of having multiple objects stored in the same partition. For heavy workloads, this can cause I/O issues. By using a random prefix, you increase the chance of S3 distributing the objects over multiple partitions, distributing the I/O workload.

## S3 Performance updated
In July 2018, AWS increased S3 performance:
- 3,500 PUT requests per second
- 5,50 GET requests
- Negates previous guidance to randomise object key names
- Logical and sequential naming can be used without performance implications
