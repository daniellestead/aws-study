## Route53 Lab

#### What is Route53?
Route53 is Amazon's DNS service. It allows you to map your domain names to:
  - EC2 instances
  - Load balancers
  - S3 buckets

#### Creating a domain
1. Select Route53 in services. We click 'Get started now' in the DNS management
tab. Then we 'Create hosted zone'.
2. Before we create the hosted zone, we click on 'Registered domains' in the
sidebar to register a domain. If we click on 'Register domain', we get taken to
a page where we can pay for an available domain name. The .com domains are $12.
We need to fill out the registrant information and hit 'Submit'.
3. Once we've agreed to the T&C's, AWS sends a verification email that we need
to open before continuing.
4. It can take up to three days to register the domain. The progress for this is
under 'Pending requests' in the sidebar.

#### Creating a record set
1. Go to 'Dashboard' in the sidebar and hit 'Hosted zones' under DNS management.
We should be able to see our domain here.
2. Hit 'Go to record set'. This is where we see our DNS records. Select 'Create
record set' so we can create an A record - which essentially maps a domain name
to the IPv4 address of the computer hosting the name.
3. We are using a naked domain name, which means using the domain *without* the
www. part. This is sometimes referred to as the **zone apex record**. In order
to do this we have to use an alias, so check 'Yes' next to 'Alias'.
4. Under 'Alias Target', we can select the type of target for the alias. These
targets include ELB's, S3 buckets etc. We need to create an ELB for this.

#### Creating an ELB
1. Go to EC2 in services. We still have the instance running from the earlier
lab. We click 'Load balancers' in the sidebar.
2. Select 'Create load balancer', we are going to create an applicaion load
balancer. Give the load balancer a name and make sure the scheme is
internet-facing and the IP address type is IPv4.
3. A listener is a process that checks for connection requests, using the
protocol and port configured. HTTP is on port 80 and HTTPS is also available on
port 443. If you don't want to use SSL you can delete the HTTPS listener.
4. The availability zones show where we can base our ELB. If we select all
availability zones we get maximum redundancy.
5. We then configure a security group. We assign the security group we created
in the last lab and continue to routing configuration.
6. The load balancer routes requests to the targets in this target group using
the ports and protocols specified. Each target group can be associated with only
on load balancer. We create a new target group, giving it a name. The target
type indicates whether the targets are registered using instance IDs or private
IP addresses. We use instance ID's in this lab.
7. Under health checks, we add the path of the webpage we create earlier
(/index.html) and leave everything else as default.
8. To register our targets, we click on the instance we created under
'Instances' and select 'Add to registered'.
9. Hit 'Review' followed by 'Create'. This might take a while to provision.
10. We can see the health status of the target under 'Target groups' in the
sidebar, if the target is healthy, the ELB has reached the index.html page we
created.

#### Implementing the record set
1. Go back to the Route53 service and create a hosted zone. Now we have a domain
registered, we then repeat the steps to create a record set although now we can
point our alias target at the ELB we created. We leave everything else as
default and hit create.
2. If we go to the domain name we created on the web, we see we have created a
working website, behind an application load balancer which is spread across
multiple availability zones. When we go to this domain, that's basically sending
traffic to this application load balancer which is sending traffic to the EC2
instance.
