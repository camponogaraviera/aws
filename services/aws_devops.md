<div align='center'>
  <h1> CI/CD </h1>
</div>

# Table of Contents

- [CodePipeline](#codepipeline)
- [CodeBuild](#codebuild)
- [CodeDeploy](#codedeploy)

---

# [CodePipeline](https://aws.amazon.com/codepipeline/faqs)

AWS CodePipeline is a continuous integration and continuous delivery (CI/CD) service that automates the build, test, and deploy phases of the release process. It helps streamline software updates by integrating with other AWS services such as `CodeBuild`, `CodeDeploy`, `Beanstalk`, `CloudFormation`, `Lambda`, and third-party tools (e.g., `GitHub`, `Jenkins`). Pipelines are defined as a series of stages, allowing for flexible automation and fast, reliable delivery of application updates.

"[AWS CodePipeline is a continuous delivery service that enables you to model, visualize, and automate the steps required to release your software. With AWS CodePipeline, you model the full release process for building your code, deploying to pre-production environments, testing your application and releasing it to production. AWS CodePipeline then builds, tests, and deploys your application according to the defined workflow every time there is a code change. You can integrate partner tools and your own custom tools into any stage of the release process to form an end-to-end continuous delivery solution.](https://aws.amazon.com/codepipeline/faqs/#topic-0)" —AWS.

# [CodeBuild](https://aws.amazon.com/codebuild/faqs/)

"[AWS CodeBuild is a fully managed continuous integration service in the cloud. CodeBuild compiles source code, runs tests, and produces packages that are ready to deploy. CodeBuild eliminates the need to provision, manage, and scale your own build servers. CodeBuild automatically scales up and down and processes multiple builds concurrently, so your builds don’t have to wait in a queue. You can get started quickly by using CodeBuild prepackaged build environments, or you can use custom build environments to use your own build tools. With CodeBuild, you only pay by the minute.](https://aws.amazon.com/codebuild/faqs/#topic-0)" —AWS.

# [CodeDeploy](https://aws.amazon.com/codedeploy/faqs/)

AWS CodeDeploy is a fully managed deployment service that automates software deployments to a variety of compute services, such as Amazon EC2, AWS Fargate, Lambda, and on-premises servers. It supports rolling updates, blue (current production)/green (staging/new version) deployments, and automatic rollback (if issues arise with the new version), helping ensure high availability and minimal downtime during updates.

"[AWS CodeDeploy is a service that automates code deployments to any instance, including Amazon EC2 instances and instances running on-premises. AWS CodeDeploy makes it easier for you to rapidly release new features, helps you avoid downtime during deployment, and handles the complexity of updating your applications. You can use AWS CodeDeploy to automate deployments, eliminating the need for error-prone manual operations, and the service scales with your infrastructure so you can easily deploy to one instance or thousands.](https://aws.amazon.com/codedeploy/faqs/)" —AWS.
