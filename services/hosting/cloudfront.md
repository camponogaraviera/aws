<div align='center'>
  <h1> 1. Frontend & Hosting </h2>
  <h2> 1.3 Content Delivery Network (CDN) </h2>
</div>

# Table of Contents

- [About](#about)

---

# About

[Amazon CloudFront](https://aws.amazon.com/cloudfront/) is the Amazon [Content Delivery Network (CDN)](https://github.com/camponogaraviera/full-stack-roadmap/blob/main/system_design_and_infrastructure/07_cdn.md) used to retrieve static data with low latency (milliseconds). It routes client static requests to an S3 bucket for retrieval of static data, and routes client dynamic requests to the API Gateway for retrieval of dynamic (server-side) data.
