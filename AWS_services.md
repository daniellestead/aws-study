| Service | Notes | Done |
|:-------:|:-----:|:----:|
| IAM | Users/groups/roles & differences between policies (inline, managed and customer managed policies) | |
| EC2 | Difference between load balancers (application -7, network -4, classic -4 & 7). | |
| Route53 | DNS & domain names. | |
| S3 | Storage tiers (IA, reduced redundancy, glacier etc). | |
| RDS | Read replicas - read only copy of DB. | |
| Elasticache | Redis - supports multi-AZ and master/slave & Memcached - simple caching. | |
| CORS | Cross origin resource sharing. | |
| CloudFront | Speeds up web content by delivering through edge locations. | |
| Lambda | | |
| API Gateway | Creates interface for clients and allows you to call Lambdas. | |
| DynamoDB | Query (find only by primary key) and scan types, noQSL. | |
| KMS | Create and manage encrypted keys. | |
| Cognito | User pools -provides web identity federation & Identity pools - enable creation of identities that are going to be unique between users (temp creds etc). | |
| SNS vs SQS | SNS pushes messages while SQS will be pulled. | |
| Kinesis | Know differences between Kinesis Steams and Firehose (Firehose has no shards while Streams does & you use Lambda with Firehose). | |
| CodePipeline | Pipeline automates software release process. | |
| CodeBuild | Runs a set of commands that you define. | |
| CloudWatch | Used to monitor things like: compute, storage, database and analytics (does not monitor RAM). | |
| CloudTrail | Monitors API calls in AWS. | |
| Systems manager | More for SYSops admin - gives visibility and control over AWS infrastructure. | |
| AWS config | Records the state of services and notifies you if there is a change. | |
| VPC | Know the difference between a network access control list and a security group & you cannot have transitive peering across VPCs. | |
| ECS | Elastic container service. | |
