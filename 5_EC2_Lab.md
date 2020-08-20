## EC2 Lab

#### Launching an instance
1. If we navigare to the EC2 service, we can click 'Launch instance'. Instances are
created from 'Amazon machine images'. We use the Amazon Linux AMI for this lab.
2. It then takes us to a page where we choose the instance type, where we choose T2
micro.
3. The third step is to choose the instance configuration options. This is
where we can change the number of instances we are creating, as well as the
network vpc, pricing options and more. We go with the default network vpc,
subnet and auto-assign public IP.
Detailed cloudwatch monitoring monitors the instance every minute, rather than
every 5 minutes.
4. We are then asked to add storage to the instance, and we first need to choose
the root device storage. We just used the general purpose SSD for this lab. We
can add additional volumes in this step page too.
5. Then we add tags, which is a case-sensitive key-value pair, such as name =
MyWebServer.
6. Then we configure the security groups, which is like a virtual firewall where
we allow traffic in and out of the instance. We create a new security group
called 'MyWebDMZ' and set the type to SSH. We then enable the instance to be
SSH'd into from 'Anywhere' under the 'Source'. We create another type to allow
HTTP requests, and we want to allow HTTP access from anywhere. We can then hit
Review and launch'.
7. This is where we create a new public key and private key pair. We enter a
name for the key and select 'Download key pair'. This is a .pem file. We can
then hit 'Launch instance'.

#### Connecting to an instance
If we select 'Instances' in the side-bar menu, it shows the running instances.
We need to copy the IPv4 Public Key.

We then open up terminal:

1. First cd into the folder containing the .pem file.
2. Allow access to the file:

  ```$ chmod 400 <keypair>.pem```
3. SSH into instance:

  ```$ ssh ec2-user@<IPv4 Public Key> -i <keypair>.pem```
4. Elevate permissions to root to become a super-user:

  ```$ sudo su```
5. Update operating system to include relevant packages:

  ```# yum update -y```
6. Install Apache:

  ```# yum install httpd -y```
7. Start Apache service:

  ```# service httpd start```
8. If the instance reboots, we want Apache to start up again immediately, so we
type in:

  ```# chkconfig httpd on```
9. To check if the service is running, we type:

  ```# service httpd status```
10. When we installed Apache, we created a directory, which is the root
directory: of our web server:

  ```# cd /var/www/html```
11. Create web page:

  ```# nano index.html```
12. Write html script, hit Ctrl + X to save and quit.

```<html><body><h1>Hello world</h1></body></html>```
13. If we type the IP address of the instance into the web browser, we can see
the 'Hello world' html header.

But how do we register a domain name and have it point at that public IP?
First we need to create an application load balancer.
