1. AWS has regions all around the world, each region can named as us-east-1, ap-south-1, ap-south-2 
2. A region is a cluster of data centers
3. Most of the AWS services are region specific

How to choose an AWSW Region 

* Compliance with data and governance and legal requirements, like data never leaves the region without our explicit permission 
* Proximity to customer is going to reduce latency 
* Available Services with in the region 
* Pricing may varies one region to another region 

## AWS Availability Zones

 * Each region has many availability zones usually min is 3 max is 6 
 * Each availability zone (AZ) is one or more separate data centers with redundant power, networking, and connectivity, but they’re connected with high bandwidth, ultra-low latency networking
* These AZ's Separated each other, so that each AZ's is isolated form natural calamities 

## AWS Points of Presence (Edge Locations)

 * Amazon has 400+  Edge Locations & 10+ Regional Caches in 90+ cities across 40+ countries
 * Content is delivered to end users with lower latency

## AWS Global Service 

* Identity and Access Management (IAM)
* Route 53 (DNS service)
* CloudFront (Content Delivery Network)
* WAF (Web Application Firewall)
