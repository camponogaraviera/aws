<div align='center'>
  <h1>Compute</h1>
</div>

# [Amazon Elastic Compute Cloud (EC2)](https://aws.amazon.com/pt/ec2/)

EC2 is the Enterprise level for systems that will likely scale with multiple web servers.

---

# [AWS Lambda](https://aws.amazon.com/pm/lambda)

"Compute service that runs your code in response to events and automatically manages the compute resources." —[AWS](https://aws.amazon.com/pm/lambda). 

AWS Lambda is completely serverless (maintained by AWS), as opposed to AWS EC2 which is maintained by AWS and the user. This service allows users to run their functions/code snippets (in JavaScript, Java, or Python) on the cloud. Lambda Triggers are then set up to execute this Lambda function. This function can return a value, write/read and modify data to either S3 or DynamoDB, or connect to other services such as API Gateway, Cognito Sync (mobile), Kinesis, SNS, CodeCommit, CloudWatch Events/Logs, Alexa Skills/Smart Home, AWS IoT, CloudFront...

## Use cases

- Lambda functions are used to/for:
  - Model microservices.
  - Reply to triggers during events (changes in data, system state).
  - Create an event generator that listens to events from DynamoDB streams.
  - Machine learning data preprocessing.
  - Communication between the API and other Amazon services (S3, Kinesis, SNS, Step Functions, Bedrock...).
 
## Scaling

["By default, Lambda provides your account with a total concurrency limit of 1,000 concurrent executions across all functions in an AWS Region."](https://docs.aws.amazon.com/lambda/latest/dg/lambda-concurrency.html)
