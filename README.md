********** Kprofile IAC ***************

This repository contains the Infrastructure as Code (IaC) for the Kprofile project using Terraform and GitHub Actions.

Workflow Overview
This workflow is triggered by:

Push events on the main and stage branches affecting files in the terraform/ directory.

Pull request events on the main branch affecting files in the terraform/ directory.

The workflow applies Terraform changes to manage AWS resources and configure the Kubernetes cluster.

Environment Variables
The following environment variables are used in the workflow:

AWS_ACCESS_KEY_ID: AWS Access Key ID for deployment to AWS.

AWS_SECRET_ACCESS_KEY: AWS Secret Access Key for deployment to AWS.

BUCKET_TF_STATE: S3 bucket for storing the Terraform state.

AWS_REGION: AWS region (default: us-east-2).

EKS_CLUSTER: EKS cluster name (kprofile-eks).

Infrastructure Components
The Terraform configuration defines the following infrastructure components:

AWS EKS Cluster: A managed Kubernetes cluster.

AWS S3 Bucket: Used for storing the Terraform state.

AWS IAM Roles: Roles and policies required for the EKS cluster and other AWS resources.

Kubernetes Resources: Various Kubernetes resources such as deployments, services, and an ingress controller.

Key Points
Automatic Triggers:

The workflow is automatically triggered by pushes and pull requests affecting the Terraform code.

Terraform Initialization and Validation:

The workflow initializes the Terraform configuration, formats, validates, and creates an execution plan.

Terraform Apply:

If the branch is main and the event is a push, the workflow applies the Terraform changes.

AWS Credentials Configuration:

AWS credentials are configured to interact with AWS services.

EKS Cluster Configuration:

The kubeconfig file is updated for the EKS cluster to enable interaction with the Kubernetes cluster.

Ingress Controller Installation:

An NGINX ingress controller is installed in the Kubernetes cluster to manage external access to the services.

How to Use
Clone the repository:

sh
git clone <repository-url>
cd <repository-directory>
Set up secrets in the GitHub repository:

AWS_ACCESS_KEY_ID

AWS_SECRET_ACCESS_KEY

BUCKET_TF_STATE

Push or create a pull request with changes in the terraform/ directory:

The workflow will automatically run based on the triggers defined.
