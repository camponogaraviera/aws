<div align='center'>
  <h1> 3. Networking </h1>
  <h2> Amazon API Gateway </h2>
</div>

# Table of Contents

- [About](#about)
- [API Gateway Quotas](#api-gateway-quotas)
  - API Gateway WebSockets Quotas

---

# About

[Amazon API Gateway](https://aws.amazon.com/api-gateway/) is a managed service that bridges the interaction between clients and backend services. It routes incoming traffic (requests) to other AWS services, handles thousands of concurrent API calls, throttling (limit of RPS), monitoring, authorization (via IAM), authentication (via Cognito), and access control.

Has support for [CORS](https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-cors.html), containerized, and serverless workloads. More about CORS [here](https://github.com/camponogaraviera/full-stack-roadmap/blob/main/backend/api/cors.md).

Can be used to build:

1. [HTTP APIs](https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api.html).
2. [REST APIs](https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api-vs-rest.html);
3. [WebSocket APIs](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-websocket-api-overview.html).

Amazon API Gateway can be used in two modes:

1. Proxy: API Gateway simply forwards the request to a backend Lambda function without modifying it.

2. Mapping: maps/transforms/manipulates requests to a format specific to the lambda function.

# [API Gateway Quotas](https://docs.aws.amazon.com/apigateway/latest/developerguide/limits.html)

API Gateway has:

- A default quota of 10k requests per second (RPS) per account, per region across HTTP APIs, REST APIs, and WebSocket APIs. This represents throughput, how many requests can be received and routed per second. It does not refer to concurrency, which represents the number of in-flight requests being processed at once. This quota can be increased.

- A timeout limit of 29 seconds. However, [it can be extended](https://aws.amazon.com/tw/about-aws/whats-new/2024/06/amazon-api-gateway-integration-timeout-limit-29-seconds/).

API Gateway does not enforce a quota on concurrent connections.

## [API Gateway WebSockets Quotas](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-execution-service-websocket-limits-table.html)

API Gateway WebSockets has:

- A default rate limit of 500 new WebSocket connection requests per second per account, per region. One can only start up to 500 new WebSocket connections each second. If the app tries to open more than this many connections simultaneously, some connections will be throttled or rejected. For example, the 501st user trying to log-in simultaneously must retry to establish a connection.

- A maximum connection duration (lifetime) of 2 hours.
