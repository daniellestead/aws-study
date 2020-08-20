## Version control with Lambda

When using versioning in AWS LAmbda you can publish one or more versions of your function. As a result, you can work with different variations of the Lambda function in the development workflow (ie. test and production).

Each function has a unique ARN number, so after you publish a version, that ARN is immutable. The `$LATEST` shows the latest version.

Qualified ARN: `arn:aws:lambda:aws-region:acct-id:function:helloworld:$LATEST`

Unqualified ARN: `arn:aws:lambda:aws-region:acct-id:function:helloworld`

Aliasing: We can map the version number of the function to an alias (ie. PROD). This is useful for development because when the $LATEST code is updated, this can be published as a new improved version 2, then this version can be promoted to production by remapping the PROD alias to point to version 2. This is easily rolled back too.

EXAM tips:
- Can have multiple versions.
- Latest version uses $LATEST.
- Qualified version with use $LATEST, unqualified will not.
- Versions are immutable (can't be changed).
- It is possible to split traffic across 2 versions of a Lambda function, based on % weights (not $LATEST version, instead create an alias for $LATEST).
