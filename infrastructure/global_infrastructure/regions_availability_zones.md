<div align='center'>
  <h1> AWS Global Infrastructure </h1>
  <h2> Regions & Availability Zones </h2>
</div>

# Table of Contents

- [How are regions and AZs structured?](#how-are-regions-and-azs-structured)
- [High availability and fault isolation](#high-availability-and-fault-isolation)
- [References](#references)

---

# How are regions and AZs structured?

Amazon Web Services (AWS) operates 39 geographic regions globally, containing a total of 124 Availability Zones (AZs) [1].

## Regions

A region is a separate geographic area (e.g. North America, South America, Europe, Middle East, Africa, Asia Pacific, Australia, and New Zealand), identified by a code such as us-east-1, sa-east-1, etc.

- Regions are isolated from each other: separate control planes and separate infrastructure. A failure in one region should not affect another.

- Data does not leave a region unless you explicitly move or replicate it. This matters for data residency and compliance (e.g. GDPR).

- Not every service, instance type, or feature is available in every region, and prices differ between regions.

## Availability Zones

An Availability Zone (AZ) is one or more discrete data centers inside a region, with redundant power, networking, and cooling.

- Each region has multiple AZs.

- AZs in a region are physically separated by a meaningful distance so that a local disaster (fire, flood, power outage) is unlikely to hit two AZs at once.

---

# High availability and fault isolation

## Service scope: global, regional, zonal

- Global (data is served from the edge): IAM, Route 53, and CloudFront.

- Regional (AWS distributes it across AZs): S3, DynamoDB, SQS, Lambda, Elastic Load Balancing, and API Gateway.

- Zonal (lives in one AZ, you must add redundancy): EC2 instances, EBS volumes, subnets, and single-AZ RDS.

---

# References

[1] https://aws.amazon.com/about-aws/global-infrastructure/regions_az/