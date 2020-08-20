## EC2 Summary

#### Pricing types
* On demand - fixed rate, no commitment.
* Reserved - capacity reservations & discount on 1 or 3 year terms.
* Spot - bid for price you want.
 - If AWS terminates, you don't pay for the hour but if you terminate, you pay
for full hour.
* Dedicated host - physical EC2 server.

**F** - **F**PGA

**I** - **I**OPS

**G** - **G**raphics

**H** - **H**igh disk throughput

**T** - cheap general purpose (**T**2 micro)

**D** - **D**ensity

**R** - **R**AM

**M** - **M**ain choice for general purpose

**C** - **C**ompute

**P** - Graphics (**P**ics)

**X** - **X**treme memory

****

#### Storage types

**SSD**
 * General purpose SSD - balances price and performance.
 * Provisioned IOPS SSD - highest performance.

**Magnetic**
* Throughput optimised HDD - low cost, can't be a boot volume.
* Cold HDD - lowest cost, can't be a boot volume.
* Magnetic - legacy, *can* be a boot volume.

#### Elastic load balancers
* Application load balancer
* Network load balancer
* Classic load balancer


* 504 error means gateway timeout, so the app didn't respond.
  - Trouble shoot, is it the web server or the database server?


* If you need the IPv4 address of end user, look for the X-Forwarded-For header.

#### Route53

* Amazon's DNS service.
* Allows you to map domain names to:
  - EC2 instances
  - Load balancers
  - S3 buckets
