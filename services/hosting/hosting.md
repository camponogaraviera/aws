<div align='center'>
  <h1> 1. Frontend & Hosting </h2>
  <h2> 1.2 Hosting Options </h2>
</div>

# Table of Contents

- [Amazon S3](#amazon-s3)
- [Amazon CloudFront + Amazon S3](#amazon-cloudfront--amazon-s3)
- [AWS Amplify](#aws-amplify)
- [Hosting Pipeline](#hosting-pipeline)

# [Amazon S3](https://aws.amazon.com/s3/)

Amazon S3 is suitable for hosting **static websites** with no server-side scripting, only client-side. However, it requires the S3 bucket to be publicly readable (not recommended). It does not provide an SSL/TLS certificate for endpoints (HTTPS).

**Note:** Static websites mean HTML/CSS/JavaScript files with no backend logic and possibly APIs called from elsewhere. Example: landing page websites.

# [Amazon CloudFront + Amazon S3](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/getting-started-cloudfront-overview.html)

The combination of `CloudFront + S3` can be used to host static websites. While S3 stores the static content (HTML, CSS, JS, images, fonts) of static websites, CloudFront serves it.

- Pros: Fine-grained control over access, caching, and performance.

- Cons: More DevOps overhead. Unlike AWS Amplify, it lacks built-in auth and CI/CD. Developers must manually build authentication, payments, and deployment pipelines.

# [AWS Amplify](https://aws.amazon.com/amplify/)

AWS Amplify is a development platform that provides a fully managed hosting solution for **static websites**, including progressive web apps (PWAs). 

[AWS Amplify Hosting](https://aws.amazon.com/amplify/hosting/) primarily supports static and server-side rendered web applications. It supports server-side rendering (SSR) for frameworks such as Next.js, where the App's content can be pre-rendered on the server before being delivered to the client. It also provides **DNS integration** with AWS Route 53 and SSL/TLS certificates (HTTPS).

AWS Amplify has a no-code alternative ([Amplify Studio](https://aws.amazon.com/pt/amplify/studio/)) for building the frontend of web apps by using a visual interface.

- AWS Amplify does not host native mobile applications as they are packaged and distributed through app stores (e.g., Apple App Store, Google Play Store).

- AWS Amplify supports web frontend integration with serverless backend APIs (e.g., built with Lambda + API Gateway, Cognito, etc.).

It uses `AWS CloudFormation` under the hood to **integrate the frontend** of static web apps, server-rendered web apps (built with Angular CLI or ReactJS + Next.js/Vue.js/Nuxt.js), native mobile apps (Kotlin for Android, Swift for iOS), and cross-platform mobile apps (Flutter or React Native) **with a serverless backend** that might include `Lambda + API Gateway` (for RESTful APIs) or `AppSync` (for GraphQL APIs), `Cognito` (for authentication), `DynamoDB` (for database), and a `hidden EC2 instance` (for compute).

- AWS Amplify also supports web frontend integration with a classic RESTful API server (e.g., built with Node.js + Express.js).

In this case, the frontend is hosted on Amplify, while the backend is deployed on Elastic Beanstalk (ideal for monolithic), or Fargate (ideal for microservices) through ECS/EKS (orchestration), or directly on EC2 instances.

# Hosting Pipeline

1. Push your React Web App to GitHub/GitLab.

2. Create an Amplify app -> connect repo.

3. Use Amplify to host the frontend application on S3 and serve it through CloudFront with CI/CD. 

4. Use Elastic Beanstalk (monolithic) or Fargate (microservices, containerized) to deploy **server-based** backends (e.g., built with Express.js).

5. Configured CORS so that requests from the Amplify-hosted frontend can be send to the backend API.

6. Store environment variables (keys, credentials, etc.) inside AWS. Use AWS Amplify console for frontend build-time variables and CI/CD configuration, and AWS Elastic Beanstalk console for backend API secrets and database credentials. Optionally, store deployment credentials in GitHub Actions secrets when using GitHub Actions.