# terraform-aws-production

Production-ready Terraform configuration for deploying AWS infrastructure.

## Overview
This repository contains Terraform code and modules to provision production AWS infrastructure (VPC, networking, IAM, ECS/EKS, RDS, S3, etc.).

## Install Terraform

### macOS (Homebrew)
```
brew tap hashicorp/tap
brew install hashicorp/tap/terraform
```

### Linux (APT)
```
sudo apt-get update && sudo apt-get install -y gnupg software-properties-common curl
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmour -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install terraform
```

### Windows
- Download installer from https://www.terraform.io/downloads.html or use Chocolatey:
```
choco install terraform
```

Verify installation:
```
terraform version
```

## Clone the project
Replace the URL with the repository location (SSH or HTTPS).
```
git clone git@github.com:<your-org>/terraform-aws-production.git
cd terraform-aws-production
```
or
```
git clone https://github.com/<your-org>/terraform-aws-production.git
cd terraform-aws-production
```

## Running the code

### Configure AWS credentials
Option A — environment variables:
```
export AWS_ACCESS_KEY_ID=...
export AWS_SECRET_ACCESS_KEY=...
export AWS_DEFAULT_REGION=us-east-1
```

Option B — AWS CLI named profile:
```
aws configure --profile myprofile
export AWS_PROFILE=myprofile
```

### Initialize and apply
Initialize the working directory:
```
terraform init
```

Validate configuration:
```
terraform validate
```

Create or review a plan:
```
terraform plan -var-file="envs/prod/terraform.tfvars"
```

Apply changes:
```
terraform apply -var-file="envs/prod/terraform.tfvars"
```
Use `-auto-approve` only in automated CI where you have explicit approvals.
