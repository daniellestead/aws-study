## CloudFront
Amazon's content delivery network

#### What is a CDN?
A content delivery network is a system of distributed servers(network) that
deliver webpages and web content to a user based on the geographic location of
the user, origin of the webpage and a content delivery server.

If users are far away from the location the webpage is hosted, they might
experience latency issues. We can introduce **edge locations**, which is a
collection of servers in geographically dispersed locations that keep a cache of
copies of object. This means users can access content from the edge locations.

Once the request is made, the edge location forwards that to the host and then
saves that request. The caches clear themselves once the 'time to live' is up.
The cache can be manually cleared, although this incurs a cost.

**Edge location** - location where content is cached and can also be written
(not regions or AZ's).

**Origin** - the origin of all files the CDN will distribute, can be S3 bucket,
EC2 instance, ELB or Route53.

**Distribution** - the name given to the CDN, which consists of a collection of
edge locations.

**Web distribution** - typically used for websites (only S3 or HTTP/HTTPS
requests)

**RTMP** - (real time messaging protocol) used for media streaming.

CloudFront is optimised to work with other AWS services, such as S3, EC2, ELB
and Route53. Also works seamlessly with any non-AWS origin server, which stores
the original versions of your files.

#### Transfer acceleration
This takes advantage of CloudFront's globally distributed edge locations. As the
data arrives at an edge location, data is routed to S3 over an optimised
network path.
