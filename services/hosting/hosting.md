<div align='center'>
  <h1> 1. Frontend & Hosting </h2>
  <h2> 1.1 Hosting Options </h2>
</div>

# Table of Contents

- [Hosting vs Deployment](#hosting-vs-deployment)
- [Amazon S3](#amazon-s3)
- [AWS Amplify](#aws-amplify)
  - Deployment
- [Amazon CloudFront + Amazon S3](#amazon-cloudfront--amazon-s3)

# Hosting vs Deployment

- Hosting is the process of storing and serving the application to end-users. The hosting service provider makes the deployed application accessible to end-users (e.g., via a URL) and manages uptime/scaling.

  - **Services**: Amplify or S3+CloudFront.

- Deployment is delivering/pushing the application's code to a runtime environment (server, container, cloud provider, or edge network) where it can be executed. It may also involve pipelines and infrastructure provisioning.
  - **Tools/Frameworks**: AWS SAM and Serverless Framework.
  - **Services**: CodeDeploy, CodePipeline, App Runner.

# [Amazon S3](https://aws.amazon.com/s3/)

Amazon S3 is suitable for hosting **static websites** with no server-side scripting, only client-side. However, it requires the S3 bucket to be publicly readable (not recommended). It does not provide an SSL/TLS certificate for endpoints (HTTPS).

**Note:** Static websites mean HTML/CSS/JavaScript files with no backend logic and possibly APIs called from elsewhere. Example: landing page websites.

# [AWS Amplify](https://aws.amazon.com/amplify/)

AWS Amplify is a development platform that provides a fully managed hosting solution for **static websites**, including progressive web apps (PWAs). It supports server-side rendering (SSR) for frameworks such as Next.js, where the App's content can be pre-rendered on the server before being delivered to the client. It also provides **DNS integration** with AWS Route 53 and SSL/TLS certificates (HTTPS).

Amplify has a no-code alternative ([Amplify Studio](https://aws.amazon.com/pt/amplify/studio/)) for building the frontend of web apps by using a visual interface.

**Note:** HTTPS relies on the TLS protocol (previously on SSL, which is now deprecated) to establish encrypted communication between the client and the server.

## Deployment

AWS Amplify Hosting primarily supports static and server-side rendered web applications. Amplify does not host native mobile applications as they are packaged and distributed through app stores (Apple App Store, Google Play Store).

Amplify uses CloudFormation under the hood to **integrate the frontend** of static web apps, server-rendered web apps (built with Angular CLI or ReactJS + Next.js/Vue.js/Nuxt.js), native mobile apps (Kotlin for Android, Swift for iOS), and cross-platform frameworks (Flutter or React Native) **with a serverless backend** that might include `Lambda + API Gateway` (for RESTful APIs), `AppSync` (for GraphQL APIs), `Cognito` (for authentication), `EC2` (for compute), and `DynamoDB` (for database).

Large-scale dynamic websites with high traffic (e.g., YouTube, Google, Facebook) require a scalable backend infrastructure (e.g., load balancer, EC2 instances, DynamoDB, S3). In this case, the frontend can be hosted on Amplify, while the backend can be deployed on Elastic Beanstalk (monolithic) or Fargate through ECS/EKS (microservices).

# [Amazon CloudFront + Amazon S3](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/getting-started-cloudfront-overview.html)

The combination of CloudFront + S3 can be used to host static websites. While S3 stores the static content (HTML, CSS, JS, images, fonts) of static websites, CloudFront serves it (but cannot host as a standalone service).

- Pros: fine-grained control over access, caching, and performance.
- Cons: more DevOps overhead. Unlike AWS Amplify, it lacks built-in auth and CI/CD. Developers must manually build authentication, payments, and deployment pipelines.
