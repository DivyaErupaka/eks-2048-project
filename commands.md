\#  Complete Command History – EKS 2048 Deployment



> Executed using Windows PowerShell (multiline uses ` backtick)



\---



\## 🔹 AWS Setup

aws configure



\---



\## 🔹 Create EKS Cluster

eksctl create cluster --name demo-cluster --region us-east-1 --fargate



\---



\## 🔹 Update kubeconfig

aws eks update-kubeconfig --region us-east-1 --name demo-cluster



\---



\## 🔹 Create Fargate Profile

eksctl create fargateprofile `

\--cluster demo-cluster `

\--region us-east-1 `

\--name alb-sample-app `

\--namespace game-2048



\---



\## 🔹 Deploy Application

kubectl apply -f https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/v2.5.4/docs/examples/2048/2048\_full.yaml



\---



\## 🔹 Verify Deployment

kubectl get pods -n game-2048

kubectl get svc -n game-2048

kubectl get ingress -n game-2048



\---



\## 🔹 Setup OIDC

eksctl utils associate-iam-oidc-provider --cluster demo-cluster --approve



\---



\## 🔹 Create IAM Policy

curl -O https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/v2.11.0/docs/install/iam\_policy.json



aws iam create-policy `

\--policy-name AWSLoadBalancerControllerIAMPolicy `

\--policy-document file://iam\_policy.json



\---



\## 🔹 Create IAM Service Account

eksctl create iamserviceaccount `

\--cluster demo-cluster `

\--region us-east-1 `

\--namespace game-2048 `

\--name aws-load-balancer-controller `

\--role-name AmazonEKSLoadBalancerControllerRole `

\--attach-policy-arn arn:aws:iam::<ACCOUNT-ID>:policy/AWSLoadBalancerControllerIAMPolicy `

\--approve



\---



\## 🔹 Helm Setup

helm repo add eks https://aws.github.io/eks-charts

helm repo update



\---



\## 🔹 Install Load Balancer Controller

helm install aws-load-balancer-controller eks/aws-load-balancer-controller `

\--namespace game-2048 `

\--set clusterName=demo-cluster `

\--set serviceAccount.create=false `

\--set serviceAccount.name=aws-load-balancer-controller `

\--set region=us-east-1 `

\--set vpcId=<your-vpc-id>



\---



\## 🔹 Verify Controller

kubectl get deployment -n game-2048 aws-load-balancer-controller



\---



\## 🔹 Get ALB URL

kubectl get ingress -n game-2048

