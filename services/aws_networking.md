<div align='center'>
  <h1>Networking</h1>
</div>

# [Route 53](https://aws.amazon.com/route53/)

Used to register a new domain.

---

# [Amazon API Gateway](https://aws.amazon.com/api-gateway/)

Amazon API Gateway is a managed service that bridges the interaction between clients and backend services. It routes incoming traffic (requests) to other AWS services, handles concurrent API calls, throttling (limit of RPS), and has support for authentication, RESTful APIs, WebSocket APIs, [CORS](https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-cors.html), containerized, and serverless workloads. More about CORS [here](https://github.com/camponogaraviera/full-stack-roadmap/blob/dev/system_design_and_infrastructure/backend/cors.md).

Amazon API Gateway can be used in two modes:

1. Proxy: API Gateway simply forwards the request to a backend Lambda function without modifying it.

2. Mapping: maps/transforms/manipulates requests to a format specific to the lambda function.

---

# [AWS WAF](https://aws.amazon.com/pt/waf/)

Is a Web Application Firewall (WAF) used to protect the API from common exploits/attacks such as SQL injection (SQLi) and cross-site scripting (XSS). AWS CloudFront connects to AWS WAF.
