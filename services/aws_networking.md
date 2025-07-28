<div align='center'>
  <h1>Networking/DNS/SSL</h1>
</div>

# Table of Contents

- [Route 53](#route-53)
- [Certificate Manager (SSL/TLS)](#certificate-manager-ssltls)
  - Installing an SSL/TLS certificate
- [API Gateway](#api-gateway)
- [WAF](#waf)

# [Route 53](https://aws.amazon.com/route53/)

Route 53 can be used to register a new `domain name`. 

Unlike `registro.br`, which is a management organization for `.br` domains (the ccTLD for Brazil), generic top-level domains (gTLDs) are managed by different registries (e.g., Verisign for .com). However, registrations for these gTLDs are typically done through accredited domain registrars or providers (e.g., AWS Route 53, [Squarespace](https://domains.squarespace.com/)), who interface with the registry on behalf of the customer.

---

# [Certificate Manager (SSL/TLS)](https://aws.amazon.com/certificate-manager/)

Use AWS Certificate Manager (ACM) to provision, manage, and deploy public and private SSL/TLS certificates.

Note: HTTPS relies on the TLS protocol (previously on SSL, which is now deprecated) to establish encrypted communication between the client and the server.

- Public Certificate: This certificate is issued by Amazon's public certificate authority (CA) and is recognized by browsers, making it the standard choice for securing public-facing websites. Public certificates issued by AWS ACM are intended for use exclusively with AWS services (CloudFront, Elastic Load Balancing, and API Gateway). ACM does not provide access or allow exporting the private key of publicly trusted certificates. However, you can export the public certificate and its certificate chain (the root and intermediate CAs) using the `GetCertificate API`. Public certificates are free.

- Private Certificate: This option is for internal or private applications where you control the trust settings (e.g., within a corporate network), and it requires setting up a private certificate authority. These certificates are typically not recognized by browsers for public websites and wouldn't automatically show the padlock icon next to the domain name of your website. Private certificates are paid.

## Installing an SSL/TLS certificate

To install an SSL/TLS certificate on a server or third-party provider, the following files are needed:

1. `certificate.crt`: This is your actual SSL certificate issued specifically for your domain.
2. `ca_bundle.crt (certificate chain)`: This is the certificate chain that links your SSL certificate to a trusted root authority. It usually contains one or more intermediate certificates.
3. `private.key`: This is the private key associated with your SSL certificate. Keep this file secure, as it is used to establish a secure connection.

To acquire these files, you should obtain a public SSL certificate from an external certificate authority (CA) that allows you to download both the certificate and private key. Some popular CA options include: 
- [Let's Encrypt](https://letsencrypt.org/getting-started/), [SSL For Free](https://www.sslforfree.com), `ZeroSSL`, `Sectigo`, or other paid providers.
- PS: CNAME records (name and value) are typically used for domain verification via DNS validation, and they are not included in the certificate export (not part of the certificate itself).

---

# [API Gateway](https://aws.amazon.com/api-gateway/)

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

---

# [WAF](https://aws.amazon.com/pt/waf/)

WAF is a Web Application Firewall (WAF) used to protect the API from common exploits/attacks such as SQL injection (SQLi) and cross-site scripting (XSS). AWS CloudFront connects to AWS WAF.
