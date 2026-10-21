<div align='center'>
  <h1> Deployment Strategies </h1>
  <h2> Elastic Beanstalk Deployment </h2>
</div>

# Table of Contents

- [Elastic Beanstalk Deployment Pipeline](#elastic-beanstalk-deployment-pipeline)

---

# Elastic Beanstalk Deployment Pipeline

Example of a deployment pipeline for a React-based web app with a RESTful API built using Node.js + Express.js.

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
