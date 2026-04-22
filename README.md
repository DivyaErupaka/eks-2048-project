\#  AWS EKS Project – 2048 Game Deployment (Fargate + ALB)



\##  Project Description

This project demonstrates deploying a containerized 2048 game application on AWS EKS using Fargate, along with ALB Ingress using AWS Load Balancer Controller.



\---



\##  Architecture

User → ALB → Ingress → Service → Pods (Fargate)



\---



\##  Tools \& Technologies

\- AWS EKS

\- Kubernetes

\- eksctl

\- kubectl

\- Helm

\- IAM \& OIDC

\- AWS Load Balancer Controller



\---



\##  Implementation Steps



\### 1. AWS CLI Configuration

Configured AWS credentials using CLI.



\### 2. EKS Cluster Creation

Created EKS cluster with Fargate profile.



\### 3. Kubernetes Deployment

Deployed 2048 application using YAML manifest.



\### 4. IAM \& OIDC Setup

Configured IAM OIDC provider for secure service account access.



\### 5. ALB Controller Setup

Installed AWS Load Balancer Controller using Helm.



\### 6. Ingress Configuration

Exposed application using ALB Ingress.



\---



\##  Application Access

