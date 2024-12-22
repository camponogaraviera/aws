<div align='center'>
  <h1>Networking/DNS/SSL</h1>
</div>

# [Route 53](https://aws.amazon.com/route53/)

Route 53 can be used to register a new `domain name`. 

Unlike `registro.br`, which is a management organization for `.br` domains (the ccTLD for Brazil), generic top-level domains (gTLDs) are managed by different registries (e.g., Verisign for .com). However, registrations for these gTLDs are typically done through accredited domain registrars or providers (e.g., AWS Route 53, [Squarespace](https://domains.squarespace.com/)), who interface with the registry on behalf of the customer.

---

# [AWS Certificate Manager (SSL/TLS)](https://aws.amazon.com/certificate-manager/)

Use AWS Certificate Manager (ACM) to provision, manage, and deploy public and private SSL/TLS certificates.

Note: HTTPS relies on the TLS protocol (previously on SSL which is now deprecated) to establish encrypted communication between the client and the server.

- Public Certificate: This certificate is issued by Amazon's public certificate authority (CA) and is recognized by browsers, making it the standard choice for securing public-facing websites. Public certificates issued by AWS ACM are intended for use exclusively with AWS services (CloudFront, Elastic Load Balancing, and API Gateway). ACM does not provide access nor allow exporting the private key of publicly trusted certificates. However, you can export the public certificate and its certificate chain (the root and intermediate CAs) using the `GetCertificate API`. Public certificates are free.

- Private Certificate: This option is for internal or private applications where you control the trust settings (e.g., within a corporate network), and it requires setting up a private certificate authority. These certificates are typically not recognized by browsers for public websites and wouldn't automatically show the padlock icon next to the domain name of your website. Private certificates are paid.

## Installing an  SSL/TLS certificate

To install an SSL/TLS certificate on a server or third-party provider, the following files are needed:

1. `certificate.crt`: This is your actual SSL certificate issued specifically for your domain.
2. `ca_bundle.crt (certificate chain)`: This is the certificate chain that links your SSL certificate to a trusted root authority. It usually contains one or more intermediate certificates.
3. `private.key`: This is the private key associated with your SSL certificate. Keep this file secure, as it is used to establish a secure connection.

To acquire these files, you should obtain a public SSL certificate from an external certificate authority (CA) that allows you to download both the certificate and private key. Some popular CA options include: 
- [Let's Encrypt](https://letsencrypt.org/getting-started/), [SSL For Free](https://www.sslforfree.com), `ZeroSSL`, `Sectigo`, or other paid providers.
- PS: CNAME records (name and value) are typically used for domain verification via DNS validation and they are not included in the certificate export (not part of the certificate itself).

---

# [Amazon API Gateway](https://aws.amazon.com/api-gateway/)

Amazon API Gateway is a managed service that bridges the interaction between clients and backend services. It routes incoming traffic (requests) to other AWS services, handles concurrent API calls, throttling (limit of RPS), and has support for authentication, RESTful APIs, WebSocket APIs, [CORS](https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-cors.html), containerized, and serverless workloads. More about CORS [here](https://github.com/camponogaraviera/full-stack-roadmap/blob/dev/system_design_and_infrastructure/backend/cors.md).

Amazon API Gateway can be used in two modes:

1. Proxy: API Gateway simply forwards the request to a backend Lambda function without modifying it.

2. Mapping: maps/transforms/manipulates requests to a format specific to the lambda function.

---

# [AWS WAF](https://aws.amazon.com/pt/waf/)

Is a Web Application Firewall (WAF) used to protect the API from common exploits/attacks such as SQL injection (SQLi) and cross-site scripting (XSS). AWS CloudFront connects to AWS WAF.
