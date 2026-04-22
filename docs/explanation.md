\#  Detailed Explanation – EKS 2048 Deployment



\## 🔹 Amazon EKS

Amazon EKS (Elastic Kubernetes Service) is a managed Kubernetes service that allows you to run Kubernetes without managing control plane infrastructure.



\---



\## 🔹 Fargate

AWS Fargate is a serverless compute engine for containers.

\- No need to manage EC2 instances

\- Pods run directly on Fargate



\---



\## 🔹 Kubernetes Components Used



\### 📦 Deployment

Manages multiple pods for the 2048 application.



\### 🌐 Service

Exposes the pods internally inside the cluster.



\### 🌍 Ingress

Provides external access using ALB.



\---



\## 🔹 AWS Load Balancer Controller

\- Automatically provisions Application Load Balancer (ALB)

\- Routes traffic to Kubernetes services

\- Integrated with AWS services



\---



\## 🔹 IAM OIDC Provider

\- Enables IAM roles for Kubernetes service accounts

\- Provides secure access to AWS resources



\---



\## 🔹 Helm

\- Package manager for Kubernetes

\- Used to install AWS Load Balancer Controller



\---



\## 🔹 End-to-End Flow



User → ALB → Ingress → Service → Pods (Fargate)



\---



\## 🔹 Outcome

\- Application deployed successfully on EKS

\- Accessible via public ALB URL

\- Fully managed and scalable setup

