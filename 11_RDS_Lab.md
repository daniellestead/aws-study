## RDS Lab

#### Creating the instance and database
1. Go to RDS in services. On the dashboard, there is a section labelled 'Create
instance'. We click on 'Launch a DB instance'.
2. We select MySQL as the database engine.
3. Leave all the instance specifications as default, but under settings we give
the instance a name (instance identifier), as well as master username and
password.
4. Under Network setting we use the default VPC and subnet group and create a
new VPC security group. Then under database options, we name the database and
lease everything else as default.
5. Leave backups on and disable enhanced monitoring and launch instance.

#### Launching a new EC2 instance
1. Use the linux AMI and a t2.micro.
2. Under Advanced details, we run the RDSBootStrap.sh script by copy pasting.
3. Configure the security group with the one we already made.
4. We can launch the instance with the existing key pair.


1. The endpoint is the DNS address for the database, as opposed to the IPv4
addresses to connect to EC2 instances.
2. Copy that endpoint and go to EC2. We can try visit the public IPv4 address.

#### Configuring the connection string
1. Ssh into the EC2 instance:

  ```
  $ ssh ec2-user@<public IP> -i <keypair>.pem
  $ sudo su
     ```
2. Check out html dir:
  ```
  # cd /var/www/html
  # ls
  ```
3. Open connect.php and update host name to RDS endpoint:
  ```
  # nano connect.php
  ```
4. Go to http://<public IP>/connect.php, but we *still need to configure the RDS
instance to use the security group we have the EC2 instance on*.
5. Allow the inbound security group we made for a MySQL server on port 3306.
6. Refresh the url, it should connect now.
