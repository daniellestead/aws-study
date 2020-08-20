## EC2 with S3 Role Lab

#### Creating an IAM role
1. Click on 'Create role' and check 'AWS service' as the trusted entity type,
since we are creating a role for AWS EC2. Hit 'Next' to attach permission
policies.
2. Remember we need to assign the least privileges needed. If we search for S3,
we can click AmazonS3FullAccess.
  - Policy documents are .json files, these **must** be understood for the exam.
3. Review the role and give it a name ('MyS3AdminAccess'). Hit 'Create role'.

#### Applying roles to EC2 instances
1. Find the EC2 instance, select it and then select 'Attach/Replace IAM Role'
under 'Instance Settings' in the 'Actions' dropdown.
2. Select the role we just created. Note this box will only populate with EC2
roles. Hit 'Apply'.

Since we configured a secret access key in credentials last lab, we will still
not be able to access S3 over the terminal. To remove these credentials, type:
(Don't forget to elevate privileges to superuser).

  ```# cd ~/.aws```

  ```# rm credentials```

You may also want to remove config:

  ```# rm config```

Go back to root directory:

  ```# cd /```

If we try to list the buckets in S3 now, we can access this.  

#### Exam tips
* Roles allow you to avoid using access key ID's and secret access keys.
* Roles are preferred from a security perspective.
* Roles are controlled by policies.
* You can change a policy on a role and this will be effective immediately.
* You can attach and detach roles to running EC2 instances without having to
stop or terminate an instance.
