<div align='center'>
  <h1> 16. Machine Learning </h1>
  <h2> Amazon SageMaker </h2>
</div>

# Table of Contents

- [About](#about)

---

# About

[Amazon SageMaker](https://aws.amazon.com/pm/sagemaker) is a serverless service used to build, train, and deploy AI models.

SageMaker supports:

- Orchestration and automation of end-to-end machine learning workflows (data preprocessing, model training, evaluation, and deployment) using [SageMaker Pipelines](https://docs.aws.amazon.com/sagemaker/latest/dg/pipelines.html).

- Model pre-processing.
  - Use S3 to store raw and post-processed data.
  - Write a pre-processing script directly in a [Jupyter Notebook](https://aws.amazon.com/sagemaker/ai/notebooks/) from [SageMaker Studio](https://aws.amazon.com/sagemaker/ai/studio/) or in a Lambda function.
- Model training.
  - Write a training script directly in a jupyter notebook cell or upload it to an S3 bucket.
  - Create a training job that SageMaker will run on managed EC2 instance. SageMaker handles provisioning the instances, running the script, and saving model artifacts back to S3.

- Model [Fine-Tuning](https://docs.aws.amazon.com/sagemaker/latest/dg/jumpstart-fine-tune.html) using [SageMaker JumpStart](https://docs.aws.amazon.com/sagemaker/latest/dg/studio-jumpstart.html) pre-trained models.

- Real-time Inference: Enables deployment of models as persistent HTTPS endpoints for real-time, low-latency inference.
  - [TensorRT-LLM SDK](https://docs.nvidia.com/tensorrt-llm/index.html) takes a pre-trained model and creates an optimized runtime that can be deployed to NVIDIA GPU-based instances (e.g., [EC2 G5](https://www.amazonaws.cn/en/ec2/instance-types/g5/)).
  - [AWS Neuron SDK](https://awsdocs-neuron.readthedocs-hosted.com/en/latest/index.html) compiles a pre-trained model to create an optimized runtime that can be deployed to [EC2 Inf1](https://aws.amazon.com/ec2/instance-types/inf1/) instances.

- [Batch Transform Jobs](https://docs.aws.amazon.com/sagemaker/latest/dg/batch-transform.html) for offline inference without a persistent endpoint.

# References

[1] [Preprocess data and train a machine learning model with Amazon SageMaker AI](https://docs.aws.amazon.com/step-functions/latest/dg/sample-preprocess-feature-transform.html).
