<div align='center'>
  <h1>CDN</h1>
</div>

# [CloudFront](https://aws.amazon.com/cloudfront/)

CloudFront is the Amazon [Content Delivery Network (CDN)](https://github.com/camponogaraviera/full-stack-roadmap/blob/main/system_design_and_infrastructure/07_cdn.md) used to retrieve static data with low latency (millisecond time). It routes client static requests to an S3 bucket for retrieval of static data, and routes client dynamic requests to the API Gateway for retrieval of dynamic (server-side) data.
