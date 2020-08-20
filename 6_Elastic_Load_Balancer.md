## Elastic Load Balancer

#### What is a load balancer?
A load balancer helps us balance our load over multiple servers. It makes sure
one server doesn't receive too much work and crash.

 [OSI layers](https://www.webopedia.com/quick_ref/OSI_Layers.asp)

#### Types of load balancers
* Application load balancer
  - Operates at OSI layer 7. This means application loads balancers can make
clever routing decisions, going to the application layer and load balancing based off
that.
* Network load balancer
   - Operates at OSI layer 4. Good for super fast performance and speed. This is
the most expensive AWS load balancer.
* Classic load balancer
  - Not recommended, but there for legacy systems.

##### Application load balancers
Application load balancers are best suited for load balancing of HTTP and HTTPS
traffic. They operate at layer 7 and are application-aware. They are
intelligent, and you can create advanced request routing, sending specified
requests to specific web servers.

##### Network load balancers
Network load balancers are best suited for load balancing of TCP traffic where
extreme performance is required. Operating at the connection level (layer 4),
network load balancers are capable of handling millions of requests per second,
while maintaining ultra-low latencies.

##### Classic load balancers
Classic load balancers are the legacy elastic load balancers. You can load
balance HTTP/HTTPS applications and use layer 7 specific features, such as
X-forwarded and sticky sessions. You can also use strict layer 4 load balancing
for applications that rely purely on the TCP protocol.

#### Load balancer errors
* Classic load balancer
  - If the application stops responding, the ELB responds with a 504 error
(gateway timeout). This
means the app is having issues, either a the Web Server layer or the Database
Layer. Identify where the app is failing and scale it up or out where possible.

#### X-forwarded-for header
If a user makes a DNS request from their public IP address, their request will
hit the ELB. The ELB will take that request and use the private IP address and
send that to the EC2 instance. That EC2 instance will only see that private IP
address from the ELB. This can cause problems because we can't identify where
the user is because their public IP is not handed to the EC2 instance.

The public IP address (IPv4) for the user is in the X-forwarded-for header.
