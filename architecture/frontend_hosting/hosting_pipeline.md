<div align='center'>
  <h1> Frontend & Hosting </h2>
  <h2> Hosting Pipeline </h2>
</div>

# Table of Contents

- [Introduction](#introduction)

# Introduction

1. Push your React Web App to GitHub/GitLab.

2. Create an Amplify app -> connect repo.

3. Use Amplify to host the frontend application on S3 and serve it through CloudFront with CI/CD. 

4. Use Elastic Beanstalk (monolithic) or Fargate (microservices, containerized) to deploy **server-based** backends (e.g., built with Express.js).

5. Configured CORS so that requests from the Amplify-hosted frontend can be send to the backend API.

6. Store environment variables (keys, credentials, etc.) inside AWS. Use AWS Amplify console for frontend build-time variables and CI/CD configuration, and AWS Elastic Beanstalk console for backend API secrets and database credentials. Optionally, store deployment credentials in GitHub Actions secrets when using GitHub Actions.
