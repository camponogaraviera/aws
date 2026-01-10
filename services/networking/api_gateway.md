<div align='center'>
  <h1> 3. Networking </h1>
  <h2> Amazon API Gateway </h2>
</div>

# Table of Contents

- [Amazon API Gateway](#api-gateway)

---

# [Amazon API Gateway](https://aws.amazon.com/api-gateway/)

Amazon API Gateway is a managed service that bridges the interaction between clients and backend services. It routes incoming traffic (requests) to other AWS services, handles thousands of concurrent API calls, throttling (limit of RPS), monitoring, authorization (via IAM), authentication (via Cognito), and access control.

Has support for [CORS](https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-cors.html), containerized, and serverless workloads. More about CORS [here](https://github.com/camponogaraviera/full-stack-roadmap/blob/main/backend/api/cors.md).

Can be used to build [RESTful APIs](https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api-vs-rest.html) and [WebSocket APIs](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-websocket-api-overview.html) that enable real-time two-way communication.

Amazon API Gateway can be used in two modes:

1. Proxy: API Gateway simply forwards the request to a backend Lambda function without modifying it.

2. Mapping: maps/transforms/manipulates requests to a format specific to the lambda function.

## [API Gateway Quotas](https://docs.aws.amazon.com/apigateway/latest/developerguide/limits.html)

- API Gateway (REST and HTTP APIs) has a default soft limit of 10,000 requests per second (RPS) per account per region. This represents throughput, how many requests can be received and routed per second. This allows 10k users to click on the login button simultaneously. It does not refer to concurrency, which is about in-flight (actively processed) requests been processed at once.

- API Gateway [timeout limit](https://aws.amazon.com/tw/about-aws/whats-new/2024/06/amazon-api-gateway-integration-timeout-limit-29-seconds/) has been extended beyond 29 seconds. This enables API Gateway to be used for routing requests to larger LLM models that require longer inference times.

## API Gateway WebSockets Quotas

- Default rate limit of 500 new WebSocket connection requests per second, per account, per region. Meaning one can only start up to 500 new WebSocket connections each second. If the app tries to open more than this many connections simultaneously, some connections will be throttled or rejected. For example, the 501st user trying to log-in in the same second must retry to establish a connection (API Gateway does not queue connection attempts).

- The maximum number of concurrent WebSocket connections that can remain open simultaneously per account, per region is 10,000.

- The maximum duration for a WebSocket connection in API Gateway is 2 hours. This means that API Gateway can support up to 3.6 million concurrent WebSocket connections over a 2-hour period.