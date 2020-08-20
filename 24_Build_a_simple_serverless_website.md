## Build a simple serverless website with Route53, API Gateway, Lambda and S3

#### Prerequisites
- Check domain name available
- Check bucket name is available
(These need to be the same)

1. On S3, create a bucket. Then click on the bucket, go to Properties and enable 'Static website hosting' with 'Use this bucket to host a website'.
2. Index document as 'index.html' and error as 'error.html'.
3. Go to Route53 and register a domain with the *same name as the bucket* (dot com doesn't matter).
4. Go to Lambda and create a function, which we will author from scratch.
5. Name it, choose Python 3.6 for runtime.
6. We will need to create a new role with the policy 'Simple Microservice permissions'.
7. Hit 'Create function'. You can write your code into the AWS IDE:

``` python
def lambda_handler(event, context):
    print("In lambda handler")

    resp = {
        "statusCode": 200,
        "headers": {
            "Access-Control-Allow-Origin": "*",
        },
        "body": "Danielle"
    }

    return resp
```
8. Hit 'Save'. Now we need to add triggers, these triggers are:
  - API Gateway
  - AWS IoT
  - Alexa Skills Kit
  - Alexa Smart Home
  - CloudFront
  - CloudWatch Events
  - CloudWatch Logs
  - CodeCommit
  - Cognito Sync Trigger
  - DynamoDB
  - Kinesis
  - S3
  - SNS
9. Add API Gateway as a trigger. Then scroll down to configure the trigger.
10. Create a new API and give it a name.
11. Set the deployment stage ('prod') and set the security to 'Open', then 'Add' the API.
12. Save the function. If you click the API arrow, you get the 'Invoke URL' - this won't work yet though.
13. Click on the API and you will get taken to the API Gateway page.
14. Delete the method and create a new 'GET' method.
15. Under integration type, we use Lambda function and we also need to use Lambda Proxy Integration.
16. Start typing the function name (will only work if you're in the right region). Then hit 'Save'.
17. Under Actions, hit 'Deploy API', deploy this into prod and add a description.
18. To get the Invoke URL, click on Stages, then the function method. This should print the name from the Lambda function.
19. We can use a curl command in an EC2 instance:
  `curl <invoke_URL> > myname.txt`
  The EC2 instance has called API Gateway to trigger a Lambda.
20. We can edit the GET link in the index.html to have the invoke URL.
21. There is a link in the index.html that opens an image, remember we need to make sure we have public access on the S3 bucket this is stored in.
22. Upload the index.html and error.html to the bucket.
23. Make them public!
24. Go to Route53 and click 'Hosted Zones'. The website URL should appear here.
25. Create a Record Set, and hit 'Alias'. If we click in the Alias Target, we should see the S3 website endpoint. If this doesn't show, it means your Route53 domain name and S3 bucket are not the same. Hit Create.
26. Go to the domain name. Yay!
