<div align='center'>
  <h1> 2. Backend & Deployment </h1>
  <h2> 2.4 Platform-as-a-Service (PaaS) </h2>
  <h3> AWS Elastic Beanstalk </h3>
</div>

# Table of Contents

- [About](#about)
- [Deployment Pipeline](#deployment-pipeline)

---

# About

"Elastic Beanstalk is a service for deploying and scaling web applications and services." —AWS.

[AWS Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk) is a Platform as a Service (PaaS) that automates much of the infrastructure management, including provisioning, load balancing, scaling, and monitoring. It abstracts away the underlying EC2 instances and lets you focus on your application. AWS manages the underlying EC2 instances, but it is not fully serverless.

Elastic Beanstalk (EB) is a good choice for applications with **long-running processes** (e.g., custom video processing outside MediaConvert, WebSockets, etc.) since it supports **always-on** compute (unlike Lambda, which has a 15-minute timeout).

`Beanstalk + Express.js` works well for building RESTful APIs of **monolithic architectures**, but is **less optimal for microservices** compared to `Fargate + ECS/EKS`.

# Deployment Pipeline

## Frontend

1. Push your React app to GitHub/GitLab.

2. Create an Amplify app -> connect repo -> Amplify builds and hosts it on a CDN with continuous deployments.

## Backend

1. Prepare Express.js servers for production:

- Listen on process.env.PORT. `app.listen(process.env.PORT || 3000)`
- Set environment variables (`NODE_ENV=production`) in EB (Cognito pool id, region, etc.).
- Ensure `package.json` has a working `"start"` script (EB uses it).

2. Create an Elastic Beanstalk Node.js environment and deploy.

- If you deploy from a repo, consider CodePipeline (optional) or EB CLI.
- Decide whether you want Single instance (dev) vs Load balanced + Auto Scaling (prod).

3. HTTPS behind ALB + ACM

- Request an AWS Certificate Manager (ACM) certificate (e.g., SSL/TLS) in the same region as your Beanstalk environment/ALB.
- Add an ALB listener on 443 using that certificate.
- For a custom domain (e.g., api.example.com), add Route 53 DNS configured as an Alias record, i.e., to point your domain name directly to an AWS resource (ALB, CloudFront, S3, etc.)
