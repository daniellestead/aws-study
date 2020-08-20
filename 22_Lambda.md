## Lambda

#### What is Lambda?
"Ultimate obstruction layer"

Lambda is a compute service where you can upload your code and create a Lambda function. Lambda takes care of provisioning and managing the servers you use to run the code, so you don't have to worry about operating systems, patching, scaling etc.

You can use Lambda for:
- an event-driven compute service where Lambda runs your code in response to event (such as a change in data in S3 etc.)
- a compute service to run your code in response to HTTP requests using Amazon API Gateway calls made using AWS SDKs.

Say you want to make a meme. You put a blank picture into S3. Once the picture gets into the bucket, this triggers a Lambda function that puts text over the meme and places it in the bucket. This triggers another function to return the completed meme to you.

#### What languages?

 - Node.js
 - Java
 - Python
 - C#
 - Go

#### How is Lambda priced?
- By number of requests, with first million requests being free. $0.20 per million after this.

- Duration, which is calculaed from the time your code begins until it terminates, rounded to the nearest 100ms. This price depends on how much memory you allocate to the function. You are charged $0.00001667 for every GB-second.

#### Why is Lambda cool?

- No servers, admins, etc.
- Continuous scaling.
- Super cheap.

#### Exam tips

- Lambda scales out (not up), so you can have millions of functions running at the same time but you can run out of memory.
- Lambda functions are independent, so 1 event = 1 function.
- Lambda is serverless (a compute service).
- Know what services are serverless (S3, API Gateway, DynamoDB).
- Lambda functions can trigger other functions, 1 event can = x functions if functions trigger other functions.
- Architectures can get complicated, AWS X-ray allows you to debug what's happening.
- Lambda can do things globally, you can use it to back up S3 buckets to other buckets etc.
- Know your triggers.
