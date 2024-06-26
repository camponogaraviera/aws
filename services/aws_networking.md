<div align='center'>
  <h1>Networking</h1>
</div>

# [Amazon API Gateway](https://aws.amazon.com/api-gateway/)

Responsible for redirecting incoming traffic (requests), handling concurrent API calls, and throttling (excess of RCUs and WCUs). Allows for creating RESTful and WebSocket APIs. Has [support for CORS](https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-cors.html), containerized, and serverless workloads. More about CORS [here](https://github.com/camponogaraviera/full-stack-roadmap/blob/dev/system_design_and_infrastructure/backend/cors.md).

Amazon API Gateway can be used in two modes:

1) Proxy: API Gateway simply forwards the request to a backend Lambda function without modifying it.

2) Mapping: maps/transforms/manipulates requests to a format specific to the lambda function.
   
---

# [AWS WAF](https://aws.amazon.com/pt/waf/)

Is a Web Application Firewall (WAF) used to protect the API from common exploits/attacks such as SQL injection (SQLi) and cross-site scripting (XSS). AWS CloudFront connects to AWS WAF.

---

# [Route S3](https://aws.amazon.com/route53/)

Used to register a new domain.
