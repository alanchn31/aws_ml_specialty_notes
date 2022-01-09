## Sagemaker + Docker
* All models in Sagemaker are hosted in Docker containers
	* Pre-built deep learning
	* Pre-built scikit-learn and spark ML
	* Pre-built tensorflow, MXNet, Chainer, Pytorch
		* Distributed training vis Horovod or Parameter Servers
		
* Docker
	* Containers are created from Docker images
	* Images are built using a Dockerfile
	* Images are saved in a repository - Amazon Elastic Container Registry
	* Structure of training container:
		* Everything lives in /opt/ml

## Sagemaker Neo
* Train once, run everywhere
* Optimizes code for specific devices
	* Tensorflow, MXNet,  Pytorch, ONNX, XGBoost
* Consists of a compiler and runtime

## Sagemaker Neo + IoT Greengrass
* Neo-compiled models can be deployed to a HTTPS endpoint
	* Hosted on C5, M5, M4, P3, P2
	* Must be same type of instances used for compilation
* OR Neo-compiled models can be deployed to IoT Greengrass
	* Inference at the edge with local data using model trained in the cloud
	* Use Lambda inference applications

## AWS Security
* Use Identity and Access Management (IAM), to set users for only permissions they need
* USE MFA
* Use SSL/TLS when connecting to anything
* Use Cloudtrail to log API and user activity (for auditing)
* Use encryption
* Protecting data at rest with Sagemaker
	* AWS Key Management Service (KMS) - accepted by notebooks and all Sagemaker jobs
		* Training, tuning, batch transforms, endpoints
		* Notebooks and everything under /opt/ml and /tmp can be encrypted with KMS key
* S3
	* Can use encrypted S3 buckets for training data and hosting models
	* S3 also use KMS
* Protect data in transit
	* All traffic supports TLS/SSL
	* Assign IAM roles to Sagemaker to give access to necessary resources
	* Inter-nodes training communication can be encrypted
		* Can increase training time and cost with deep learning
		* Inter-container traffic encryption
		* Enabled via console or API when setting up a training or tuning job

## Sagemaker + VPC
* Training jobs run in a Virtual Private Cloud (VPC)
* Use private VPC for more security
	* Need to setup S3 VPC endpoints
	* Custom endpoint policies and S3 bucket policies to keep secure
* Notebooks are internet enabled by default
	* Can be a security hole
	* If disabled, VPC needs an interface endpoint (PrivateLink) or NAT Gateway and allow outbound connections, for training and hosting to work

## Sagemaker + IAM