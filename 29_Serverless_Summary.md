## Serverless Summary

#### Lambda

- Scales out (not up) automatically.
- Functions are independent, 1 event = 1 function.
- Lambda is serverless.
- Know what else is serverless.
- Lambda functions can trigger other functions, so 1 event can = x functions.
- Architecture can get complicated, but X-ray allows you to debug whats happening.
- Lambda can do things globally, so you can use it to back up S3 buckets to other buckets etc.
- Know what all the services that can trigger Lambda is.

#### API gateway

- Know what it is at a high level.
- It has caching capabilities to increase performance.
- Low cost and scales automatically.
- You can throttle API gateway to prevent attacks.
- You can log results to CloudWatch.
- If you are using Javascript that uses multiple domains with API gateway, ensure you have CORS enabled.
- CORS is enforced by the client.

#### Lambda version control

- Can have multiple versions.
- Latest has $latest (qualified version will have this, unqualified will not.)
- Versions are immutable.
- Can split traffic to different versions (but not $latest unless mapped to an alias.)

#### Step functions

- Great way to visualise serverless application.
- Automatically triggers and tracks each step.
- Logs the state of each step for debugging.

#### X-Ray (tips are the same)
