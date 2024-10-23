## Setup Instuctions
##### Open Powershell in Admin mode
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

##### Install eksctl using choco
choco install eksctl

##### Install kubectl using choco
choco install kubernetes-cli

##### Install AWS CLI after downloading - Download and run the AWS CLI MSI installer for Windows (64-bit):
https://awscli.amazonaws.com/AWSCLIV2.msi
aws --version
####
################################################################################
################################################################################
Create AWS EKS clsuster
################################################################################
################################################################################

## Create EKS cluster
eksctl create cluster --name fluxDemo --node-type t2.large --nodes 1 --nodes-min 1 --nodes-max 2 --region us-west-2 

##### Get EKS Cluster service
eksctl get cluster
eksctl get cluster --name fluxDemo --region us-west-2 

##### Update Kubeconfig 
aws eks update-kubeconfig --name fluxDemo

##### Get EKS Pod data.
kubectl get pods --all-namespaces

##### Delete EKS cluster
eksctl delete cluster --name fluxDemo --region us-west-2
