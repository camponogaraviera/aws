<div align='center'>
  <h1> 16. Machine Learning </h1>
  <h2> Amazon SageMaker </h2>
</div>

# Table of Contents

- [About](#about)
- [Model Pre-Processing](#model-pre-processing)
- [Model Training](#model-training)
- [Model Fine-Tuning](#model-fine-tuning)
- [Inference Endpoints](#inference-endpoints)
- [Deployment Pipeline](#deployment-pipeline)

---

# About

[Amazon SageMaker](https://aws.amazon.com/pm/sagemaker) is a serverless service used to build, train, and deploy AI models.

SageMaker is a managed container hosting and orchestration service purpose-built for ML workloads. SageMaker supports orchestration and automation of end-to-end machine learning workflows (data preprocessing, model training, fine-tuning, evaluation, and deployment) using [SageMaker Pipelines](https://docs.aws.amazon.com/sagemaker/latest/dg/pipelines.html).

# Model Pre-Processing

- Use S3 to store raw and post-processed data.

- Write a pre-processing script directly in a [Jupyter Notebook](https://aws.amazon.com/sagemaker/ai/notebooks/) from [SageMaker Studio](https://aws.amazon.com/sagemaker/ai/studio/) or in a Lambda function.

# Model Training

- Write a training script directly in a jupyter notebook cell or upload it to an S3 bucket.

- Create a training job that SageMaker will run on managed EC2 instance. SageMaker handles provisioning the instances, running the script, and saving model artifacts back to S3.

# Model [Fine-Tuning](https://docs.aws.amazon.com/sagemaker/latest/dg/jumpstart-fine-tune.html) 

Fine-tuning can be accomplished using [SageMaker JumpStart](https://docs.aws.amazon.com/sagemaker/latest/dg/studio-jumpstart.html) pre-trained models.

# Inference Endpoints

There are four deployment options in SageMaker:

- [SageMaker Real-Time Inference Endpoint](https://docs.aws.amazon.com/sagemaker/latest/dg/realtime-endpoints.html): Is a persistent HTTPS endpoint that enables the deployment of models that require interactive (real-time), low-latency inference.
  - Pros: Standard deployment option to host and serve large foundation models such as Falcon-40B Instruct.
  - Cons: High cost with provisioned instances running 24/7.

- [SageMaker Serverless Inference Endpoint](https://docs.aws.amazon.com/sagemaker/latest/dg/serverless-endpoints.html): Ideal to deploy AI workflows that can tolerate cold starts and have idle periods between peak traffic.
  - Pros: There is no need to manage the underlying infrastructure. 
  - Cons: It does not provide GPU support.

- [SageMaker Asynchronous Inference Endpoint](https://docs.aws.amazon.com/sagemaker/latest/dg/async-inference.html): Ideal for requests with large payloads (up to 1GB), long processing times (up to one hour), and near real-time latency requirements. 
  - Pros: Provides GPU support. 
  - Cons: Not ideal for interactive inference.

- [Batch Inference Jobs](https://docs.aws.amazon.com/sagemaker/latest/dg/batch-transform.html): For offline inference on a batch of observations without a persistent endpoint, i.e., for AI workflows that do not require immediate response. 
  - Pros: Ideal for bulk inference.
  - Cons: Not ideal for deploying a model as an API.

Real-time inference, serverless inference, asynchronous inference, and batch inference. Endpoints can be queried with either `SageMaker Python SDK` or `AWS SDK for Python (Boto3)`. 

# Deployment Pipeline 

Models always run inside containers, but SageMaker typically supplies and manages those containers for you, abstracting away Kubernetes and ECS. You only build containers when customization is required (e.g., custom inference servers such as TensorRT-LLM or vLLM). When you bring your own container, you may store it in ECR, but you never deploy SageMaker endpoints through ECS or EKS.

Instead of 

```bash
Docker image -> ECR -> ECS/EKS -> EC2
```

SageMaker offers

```bash
S3 model artifacts (optional) -> Docker image (AWS-managed or custom) -> ECR (only if custom image) -> SageMaker Inference Endpoint -> Managed EC2 Instance (hidden)
```

## Examples

1. Using AWS-managed image:

```bash
AWS-managed image -> SageMaker Endpoint -> EC2 (hidden)
```

2. Using a custom image:

```bash
Docker build -> ECR -> SageMaker Endpoint -> EC2 (hidden)
```

3. Using a custom model (e.g., PyTorch):

```bash
S3 model artifacts (architecture, weights) + Inference Script -> Docker Image (Ubuntu, CUDA, TensorRT, etc.) -> ECR -> SageMaker Endpoint -> EC2 (hidden)
```

# References

[1] [Preprocess data and train a machine learning model with Amazon SageMaker AI](https://docs.aws.amazon.com/step-functions/latest/dg/sample-preprocess-feature-transform.html).

[2] [Deploy models for inference](https://docs.aws.amazon.com/sagemaker/latest/dg/deploy-model.html).
