<div align='center'>
  <h1> 4. Security </h1>
  <h2> Amazon Identity and Access Management (IAM) </h2>
</div>

# Table of Contents

- [About](#about)

---

# About

[Amazon Identity and Access Management (IAM)](https://aws.amazon.com/iam/) is used to manage `access/authorization` to AWS services (S3, DynamoDB, AWS Lambda, etc.), and resources securely. It allows you to create and manage AWS users and [groups](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups.html), and use permissions to allow and deny their access to AWS resources. IAM also supports the creation of [roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html), which can be delegated to users, applications, or services. Additionally, IAM enables you to configure user account settings, integrate with [identity providers and federation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers.html) for single sign-on (SSO), and enforce [multi-factor authentication (MFA)](https://aws.amazon.com/iam/features/mfa/) for enhanced security. IAM also allows management of encryption keys.

Note: [Federation](https://aws.amazon.com/identity/federation/) in the context of Amazon IAM refers to the practice of allowing users to access AWS resources using credentials from an external `identity provider (IdP)` instead of creating separate IAM users within AWS. This setup relies on a trust relationship between a service provider (SP), such as a service or an application that controls access to resources, and the external IdP for user authentication.
