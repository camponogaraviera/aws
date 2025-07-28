 <div align='center'>
  <h1>Identity and Access Management</h1>
</div>

# Table of Contents

- [Authentication vs Authorization](#authentication-vs-authorization)
- [Cognito](#cognito-authentication)
- [IAM](#iam-authorization)

# Authentication vs Authorization

- Authentication: is the process of verifying the identity of a user, ensuring the user is who he claims to be.

- Authorization: determines if the user has the right permission to perform specific operations, including both reading and modifying data.

# [Cognito](https://aws.amazon.com/pm/cognito) (Authentication)

AWS Cognito is a service used for `customer identity and access management (CIAM)`, it handles user authentication (sign in, sign up) and can provide role-based access to AWS services through IAM. Cognito console creates IAM roles by default to provide access to specific services such as Mobile Analytics and Amazon Cognito Sync.

AWS Cognito uses JWTs (JSON Web Tokens) for authentication and authorization.

# [IAM](https://aws.amazon.com/iam/) (Authorization)

AWS Identity and Access Management (IAM) is used to manage access/authorization to AWS services (S3, DynamoDB, AWS Lambda..), and resources securely. It allows you to create and manage AWS users and [groups](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups.html), and use permissions to allow and deny their access to AWS resources. IAM also supports the creation of [roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html), which can be delegated to users, applications, or services. Additionally, IAM enables you to configure user account settings, integrate with [identity providers and federation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers.html) for single sign-on (SSO), and enforce [multi-factor authentication (MFA)](https://aws.amazon.com/iam/features/mfa/) for enhanced security. IAM also allows management of encryption keys.

Note: [Federation](https://aws.amazon.com/identity/federation/) in the context of AWS IAM refers to the practice of allowing users to access AWS resources using credentials from an external `identity provider (IdP)` instead of creating separate IAM users within AWS. This setup relies on a trust relationship between a service provider (SP), such as a service or an application that controls access to resources, and the external IdP for user authentication.