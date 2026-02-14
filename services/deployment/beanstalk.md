<div align='center'>
  <h1> 2. Backend & Deployment </h1>
  <h2> 2.4 Platform-as-a-Service (PaaS) </h2>
  <h3> AWS Elastic Beanstalk </h3>
</div>

# Table of Contents

- [About](#about)
- [Deployment Pipeline](#deployment-pipeline)
- [References](#references)

---

# About

"Elastic Beanstalk is a service for deploying and scaling web applications and services." —AWS.

[AWS Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk) is a Platform as a Service (PaaS) that automates much of the infrastructure management, including provisioning, load balancing, scaling, and monitoring. It abstracts away the underlying EC2 instances and lets you focus on your application. AWS manages the underlying EC2 instances, but it is not fully serverless.

Elastic Beanstalk (EB) is ideal for applications with **long-running processes** (e.g., custom video processing outside MediaConvert, WebSockets, etc.) since it supports **always-on** compute (unlike Lambda, which has a 15-minute timeout).

AWS Elastic Beanstalk environments that use Auto Scaling groups rely on Amazon CloudWatch alarms to trigger scaling operations. Out of the box, Elastic Beanstalk configures scaling based on CPU utilization by default. Elastic Beanstalk itself does not natively understand GPU metrics, but it can scale on any CloudWatch metric that Auto Scaling supports.

# Deployment Pipeline

Example of a deployment pipeline for a React-based web app with a RESTful API built using Node.js + Express.js.

Note: `Elastic Beanstalk (EB)` works well for **monolithic architectures**, but is **less optimal for microservice architectures** compared to `Fargate + ECS/EKS`.

## Frontend

1. Push your React app to GitHub/GitLab.

2. Create an Amplify app -> connect repo -> Amplify builds and hosts it on a CDN with continuous deployments.

## Backend

1. Prepare the Express.js server for production:

- Listen on process.env.PORT: `app.listen(process.env.PORT || 3000)`

- Set environment variables (`NODE_ENV=production`) in EB (e.g., Cognito pool id, region, etc.).

- Ensure `package.json` has a working `"start"` script (EB uses it).

2. Create a Node.js environment in EB and deploy.

- If you deploy from a repo, consider CodePipeline (optional) or EB CLI.

3. HTTPS behind ALB + ACM

- Request an AWS Certificate Manager (ACM) certificate (e.g., [TLS](https://aws.amazon.com/compare/the-difference-between-ssl-and-tls/)) in the same region as your EB environment/ALB.

- Add an ALB listener on port 443 using that certificate. When a client request hits the ALB listener on port 443, ALB uses the ACM certificate to decrypt the traffic (TLS termination). Then, ALB forwards the request to the Elastic Beanstalk backend.

- For a custom domain (e.g., api.example.com), add Route 53 DNS configured as an Alias record, i.e., to point your domain name directly to an AWS resource (ALB, CloudFront, etc.)

# References 

[1] [Auto Scaling triggers for your Elastic Beanstalk environment](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/environments-cfg-autoscaling-triggers.html).
