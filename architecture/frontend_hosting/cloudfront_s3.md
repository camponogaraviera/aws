<div align='center'>
  <h1> Frontend & Hosting </h2>
  <h2> Hosting Options </h2>
  <h3> Amazon CloudFront + Amazon S3 </h3>
</div>

# Table of Contents

- [Introduction](#introduction)

# Introduction

The combination of [Amazon CloudFront + Amazon S3](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/getting-started-cloudfront-overview.html) can be used to host static websites. While S3 stores the static content (HTML, CSS, JS, images, fonts) of static websites, CloudFront serves it.

- Pros: Fine-grained control over access, caching, and performance.

- Cons: More DevOps overhead. Unlike AWS Amplify, it lacks built-in auth and CI/CD. Developers must manually build authentication, payments, and deployment pipelines.
