<div align='center'>
  <h1> Security & Identity </h1>
  <h2> Amazon Cognito </h2>
</div>

# Table of Contents

- [Introduction](#introduction)
- [Application Type](#application-type)
- [API Quotas Pricing](#api-quotas-pricing)
 
---

# Introduction

[Amazon Cognito](https://aws.amazon.com/pm/cognito) is a service used for `customer identity and access management (CIAM)`. 

[Amazon Cognito User Pools](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-pools.html) is an identity directory for user registration (sign-up), authentication (sign-in), and federated login for users single sign-on through an external Identity Provider (e.g., Google, Apple). Cognito handles user accounts, sign-up/sign-in flows, and issues JWTs (ID/access tokens) after successful authentication. 

Cognito can provide role-based access to AWS services through IAM and group-aware authorization policies with [Amazon Verified Permissions](https://docs.aws.amazon.com/verifiedpermissions/latest/userguide/what-is-avp.html).

---

# Application Type

When configuring an app client for a user pool, the following alternatives are available:

- **Traditional web application**: A monolithic or multi-tier server-rendered app built with Node.js, Python/Django, Ruby on Rails, PHP, or Java running on EC2, on-premises servers, or containerized platforms. It frequently uses AWS Systems Manager (SSM) Parameter Store to replace local .env files for secure configuration and secret management.

- **Single-page application (SPA)**: It specifies that the client is public and cannot safely protect a client secret. It says nothing about how the app is built, and it doesn't make the app an SPA.

- **Mobile app**: For applications built with a mobile SDK (e.g., Android or iOS).

- **Machine-to-machine application**: "Platform-independent server-to-server communications without user interaction." -AWS.

---

# [API Quotas Pricing](https://aws.amazon.com/cognito/pricing/#Pricing_table_for_Amazon_Cognito_add-ons) 

Cognito user pools provide a free tier with 10,000 monthly active users (MAUs) per month per account or per AWS organization. You can provision API rate limits for user pools above the free tier.



