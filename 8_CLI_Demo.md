## AWS CLI

1. Go to EC2 instances and select the IPv4 public IP address for the instance we
created. To connect to this, we type:

  ```$ ssh ec2-user@<public IP> -i <key-pair-file>.pem```
2. Elevate privileges to root by typing:

  ```$ sudo su```
3. List everything in S3 buckets:

  ```$ aws s3 ls```
4. Configure credentials:

  ```$ aws configure```

  We will be asked for an access key ID and secret access key. To get this, we need
to go to the IAM service in the AWS console.
5. Click on 'Users' in the sidebar and select 'Add user'. We enter a username
for the user and give them programmatic access, which enables an access key ID
and secret access key.
6. We want to set the permissions to this new user from a group, so we create a
new group and add the AdministratorAccess policy.
7. Hit 'Review'
 followed by 'Create user'.
9. We should now have the access key ID and secret access key available. We can
copy and paste these into terminal.
10. We are then prompted to add the default region name and default output
format, we hit enter to accept these defaults.
11. Again, try:

  ```$ aws s3 ls```
12. We don't have any buckets created, so we type:

  ```$ aws s3 mb s3://<valid-bucket-name>```
13. We create a text file:

  ```$ echo 'hello world' > hello.txt```
14. We can copy that text file into our S3 bucket:

  ```$ aws s3 cp hello.txt s3://<valid-bucket-name>```
15. To see the contents of the bucket, type:

  ```$ aws s3 ls s3://<valid-bucket-name>```
16. If we go the the S3 service in the AWS console, we can click on our bucket
and select our txt file. Hit 'Make public'.

#### Exam tips
* Least privilege - always give your users the minimum access required.
* Create group - assign your users to groups. Your users will automatically
inherit the permissions of the group. The groups permissions are assigned using
policy documents.
* Secret access key - you will only see this once. If you do not save it, you
can delete the key pair and regenerate it. This means you will need to re-run
aws configure.
* Do not use just one access key - do not create one access key to share with
developers. Instead create one key pair per developer. **Absolutely do not
*EVER*
put these credentials into GitHub**.
* You can use CLI on PC.
