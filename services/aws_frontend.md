<div align='center'>
  <h1>Frontend</h1>
</div>

# [AWS Amplify](https://aws.amazon.com/amplify/)

AWS Amplify is a development platform that provides a fully managed hosting solution for static websites, including progressive web apps (PWAs). It supports server-side rendering (SSR) for frameworks such as Next.js, where the App's content can be pre-rendered on the server before being delivered to the client. It also provides DNS integration with AWS Route 53 and SSL/TLS certificates (HTTPS). 

Note: HTTPS relies on the TLS protocol (previously on SSL which is now deprecated) to establish encrypted communication between the client and the server. 

Amplify has a no-code alternative ([Amplify Studio](https://aws.amazon.com/pt/amplify/studio/)) for building the frontend of web apps by using a visual interface. 

## Deployment 

Amplify can only host the frontend of `static websites`. Amplify does not host mobile applications. Mobile apps are not hosted on a server, instead, they are packaged and distributed through app stores (Apple App Store, Google Play Store).

Amplify is suitable for connecting the frontend of static web apps (built with Angular, ReactJS, Next.js, or Vue.js/Nuxt.js) and mobile applications (built with kotlin, swift, flutter, or react-native) with serverless backends, such as AppSync (GraphQL APIs), Cognito (authentication), S3 (file storage), Lambda (serverless functions), and DynamoDB.

Large-scale dynamic websites with high-traffic (e.g., YouTube, Canva, Facebook, etc.) require a backend infrastructure with scalable services (e.g., API Gateway, Step Functions, Lambda, AppSync, DynamoDB, S3, EC2, etc.). In this case, the frontend can be hosted on Amplify, while the backend can be deployed on Elastic Beanstalk. API Gateway or AppSync can be used to manage API calls between the frontend and backend.

