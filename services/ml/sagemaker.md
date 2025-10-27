<div align='center'>
  <h1> 16. Machine Learning </h1>
  <h2> Amazon SageMaker </h2>
</div>

# Table of Contents

- [Amazon SageMaker](#sagemaker)

---

# [Amazon SageMaker](https://aws.amazon.com/pm/sagemaker)

Amazon Sagemaker is a serverless service used to build, train, and deploy AI models.

SageMaker supports:

- Pipelines and Workflows: used to orchestrate and automate end-to-end machine learning workflows, including data preprocessing, model training, evaluation, and deployment. Implemented through SageMaker Pipelines.

- Model Training and [Fine-Tuning](https://docs.aws.amazon.com/sagemaker/latest/dg/jumpstart-fine-tune.html): supports training from scratch and fine-tuning through [SageMaker JumpStart](https://docs.aws.amazon.com/sagemaker/latest/dg/studio-jumpstart.html). Includes built-in support for hyperparameter optimization (HPO) to improve model performance.

- Real-time Inference: enables deployment of models as persistent HTTPS endpoints for real-time, low-latency inference. Supports instance types including GPU and AWS Inferentia (e.g., [inf1](https://aws.amazon.com/ec2/instance-types/inf1/) instances) for cost-efficient inference at scale.

- [Batch Transform Jobs](https://docs.aws.amazon.com/sagemaker/latest/dg/batch-transform.html): used for offline inference or large-scale data preprocessing without maintaining a live endpoint. Batch Transform processes input data in bulk using the same models used for real-time inference, suitable for one-time or scheduled inference tasks.
