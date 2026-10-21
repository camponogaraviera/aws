<div align='center'>
  <h1> Networking & Content Delivery </h1>
  <h2> AWS Web Application Firewall (WAF) </h2>
</div>

# Table of Contents

- [Introduction](#introduction)
- [Services](#services)

---

# Introduction

[AWS Web Application Firewall (WAF)](https://aws.amazon.com/pt/waf/) is used to protect the API from common exploits/attacks such as SQL injection (SQLi) and cross-site scripting (XSS). 

---

# Services

AWS WAF can protect several AWS services, including:

- Amazon API Gateway.
- Amazon CloudFront.
- Application Load Balancer.
- AWS AppSync.
- Amazon Cognito (certain endpoints).

For an app hosted with AWS Amplify, the traffic goes through CloudFront, so if you associate a WAF web ACL with the CloudFront distribution, WAF can inspect and block requests before they reach your hosted frontend.

For example, you can create a rate-based rule such as:

- Block an IP that sends more than 1,000 requests in 5 minutes.
- Challenge or block suspicious bots.
- Block requests from certain countries (if desired).