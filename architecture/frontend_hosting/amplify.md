<div align='center'>
  <h1> Frontend & Hosting </h2>
  <h2> Hosting Options </h2>
  <h3> AWS Amplify </h3>
</div>

# Table of Contents

- [Introduction](#introduction)

# Introduction

[AWS Amplify](https://aws.amazon.com/amplify/) is a development platform that provides a fully managed hosting solution for **static websites**, including progressive web apps (PWAs).

[AWS Amplify Hosting](https://aws.amazon.com/amplify/hosting/) primarily supports static and server-side rendered web applications. It supports server-side rendering (SSR) for frameworks such as Next.js, where the App's content can be pre-rendered on the server before being delivered to the client. It also provides **DNS integration** with AWS Route 53 and SSL/TLS certificates (HTTPS).

AWS Amplify has a no-code alternative ([Amplify Studio](https://aws.amazon.com/pt/amplify/studio/)) for building the frontend of web apps by using a visual interface.

- AWS Amplify does not host native mobile applications, as these are packaged in binaries and distributed via app stores (e.g., Apple App Store, Google Play Store). However, Amplify can store and serve static assets (e.g., images, videos, JSON files, etc.) that a mobile app can fetch.

- AWS Amplify supports web frontend integration with serverless backend APIs (e.g., Lambda, API Gateway, Cognito, etc.).

It uses `AWS CloudFormation` under the hood to **integrate the frontend** of static web apps, server-rendered web apps (built with Angular CLI or ReactJS + Next.js/Vue.js/Nuxt.js), native mobile apps (Kotlin for Android, Swift for iOS), and cross-platform mobile apps (Flutter or React Native) **with a serverless backend** that might include `Lambda + API Gateway` (for RESTful APIs) or `AppSync` (for GraphQL APIs), `Cognito` (for authentication), `DynamoDB` (for database), and a `hidden EC2 instance` (for compute).

- AWS Amplify also supports web frontend integration with a classic RESTful API server (e.g., built with Node.js + Express.js).

In this case, the frontend is hosted on Amplify, while the backend is deployed on Elastic Beanstalk (ideal for monolithic), or Fargate (ideal for microservices) through ECS/EKS (orchestration), or directly on EC2 instances.
