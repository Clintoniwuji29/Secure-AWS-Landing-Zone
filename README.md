# Secure-AWS-Landing-Zone
a production-style AWS environment with VPC, public/private subnets, NAT, IAM roles, S3, CloudTrail, CloudWatch, KMS encryption, Security Groups, and Terraform modules. This mirrors the security, governance, and guardrail work that shows up in enterprise and regulated-cloud roles.
# AWS Landing Zone with Terraform

## Overview
This project demonstrates the design and deployment of a foundational AWS network using Terraform (Infrastructure as Code). The goal is to create a secure, scalable, and repeatable cloud environment without relying on manual configuration.

---

## Architecture
- AWS VPC
- CIDR Block: 10.0.0.0/16
- Resource tagging for identification and organization

---

## Technologies Used
- AWS (EC2, VPC)
- Terraform
- AWS CLI
- HCL (HashiCorp Configuration Language)

---

## Project Structure
aws-landing-zone/
└── terraform/
└── environments/
└── dev/
└── main.tf

### 1. Configure AWS CLI
aws configure
### 2. Initialize Terraform
terraform init
### 3. Initialize Terraform
Validate Configuration
### 4. Preview Infrastructure
Preview Infrastructure
### 5. Deploy Infrastructure
terraform apply


## Key Features
Infrastructure as Code (IaC)
Automated AWS resource provisioning
Idempotent deployments
Terraform state tracking
Lessons Learned
Importance of environment setup (PATH, CLI tools)
AWS authentication and credential management
Terraform workflow (init → plan → apply)
Debugging real-world cloud deployment issues
Future Improvements
Add public and private subnets
Implement Internet Gateway and NAT Gateway
Deploy EC2 instances
Introduce Terraform modules
Add monitoring and logging 


<img width="624" height="561" alt="image" src="https://github.com/user-attachments/assets/aafdde82-c1e1-4390-b699-43333c30aaa3" />
<img width="1197" height="994" alt="image" src="https://github.com/user-attachments/assets/5fd04d35-3680-4699-bc6c-4dd8812df549" />
<img width="432" height="488" alt="image" src="https://github.com/user-attachments/assets/b5fa7f45-5f36-4416-8e51-5f855f0a1dfe" />

What I did:

You created a Terraform configuration (main.tf) defining:

AWS provider
Region (us-east-1)
Custom VPC (10.0.0.0/16)
Resource tagging
Why this matters:

Instead of clicking in AWS console:

❌ Manual
❌ Error-prone
❌ Not reusable

I used:

✅ Code-based infrastructure
✅ Version control ready
✅ Repeatable across teams
<img width="991" height="428" alt="image" src="https://github.com/user-attachments/assets/cb649d42-d708-4642-963f-e4fcc79f5471" />
<img width="1200" height="775" alt="image" src="https://github.com/user-attachments/assets/6fd26a65-a2e6-4c8a-9b4f-91dd39296e05" />
<img width="1373" height="763" alt="image" src="https://github.com/user-attachments/assets/31015da9-e8b2-4f37-bc48-067a75ce8921" />
<img width="495" height="1432" alt="image" src="https://github.com/user-attachments/assets/8814bf71-6654-43c2-b8f2-9ff26045f056" />

## What happened:
terraform init
Downloaded AWS provider (hashicorp/aws)
Created .terraform.lock.hcl
Employer value:
Ensures consistent provider versions
Prevents “it works on my machine” issues
Enables team-wide reproducibility

<img width="2718" height="762" alt="image" src="https://github.com/user-attachments/assets/97a3c229-fed9-4b18-9c31-9048e4cffa67" />
<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/11547a08-956f-48f3-921f-dfca6559e140" />
<img width="669" height="330" alt="image" src="https://github.com/user-attachments/assets/44e6235e-5ac5-4950-b013-31af9647a5a1" />
<img width="658" height="312" alt="image" src="https://github.com/user-attachments/assets/ae1da5bf-3cd7-4ce5-9324-351a80a567e4" />


Issue I hit:
Error: No valid credential sources found
Root cause:

Terraform could not authenticate to AWS.

What I did:

Configured credentials using:

aws configure

Then verified identity:

aws sts get-caller-identity
Why this is important (THIS is what interviewers want):

I demonstrated:

Cloud authentication troubleshooting
Understanding of IAM access keys
CLI-based debugging

👉 This is real cloud engineering work, not theory.

<img width="1055" height="692" alt="image" src="https://github.com/user-attachments/assets/d1ffd0c7-9d4c-4723-a4c5-656bde6075dc" />
<img width="1020" height="687" alt="image" src="https://github.com/user-attachments/assets/bdaf6a64-c5de-4b24-9d44-b718c8079356" />
<img width="1400" height="681" alt="image" src="https://github.com/user-attachments/assets/7dd0faf5-f55f-4f88-aecf-af45efb8850e" />
<img width="633" height="477" alt="image" src="https://github.com/user-attachments/assets/dfbdf1c7-ad71-43f1-bc6b-77ba67c90fbb" />

Command:
terraform plan
What it showed:
aws_vpc.main will be created
Full resource breakdown before deployment
Why this matters:
Prevents accidental changes
Enables approval workflows
Used in CI/CD pipelines

👉 This is how companies avoid outages.
<img width="1128" height="798" alt="image" src="https://github.com/user-attachments/assets/184feaa8-3e45-4f58-afcf-d50c36f682db" />
<img width="1236" height="620" alt="image" src="https://github.com/user-attachments/assets/2a7d3f22-4fd5-4fbf-915e-bb4bd73d9228" />
<img width="1000" height="500" alt="image" src="https://github.com/user-attachments/assets/f2e7bc41-3a6f-4f52-a215-cd7c07e6bf5c" />
<img width="1310" height="821" alt="image" src="https://github.com/user-attachments/assets/aaa3b79e-522a-4386-9d07-1f04a917e944" />
Command:
terraform apply
Result:
VPC created successfully
Terraform state updated
Key concept demonstrated:
Idempotency
Infrastructure matches code exactly
<img width="2179" height="1377" alt="image" src="https://github.com/user-attachments/assets/1aa45ce1-9725-46ec-a4a0-f59daae4dda4" />
<img width="2464" height="1383" alt="image" src="https://github.com/user-attachments/assets/26818dbf-24c4-4cd7-a3f5-cbec0b0e888e" />
<img width="1400" height="666" alt="image" src="https://github.com/user-attachments/assets/3e94498c-5de4-4c2f-a107-9ecaf6ab4055" />
<img width="1914" height="1013" alt="image" src="https://github.com/user-attachments/assets/f04cbb25-0fdd-459c-91d1-67eea6d1995b" />

What the screenshot proves:
VPC named "my-first-vpc" exists
Status: Available
CIDR: 10.0.0.0/16
Why this is critical:

I validated:

✅ Infrastructure actually exists in cloud
✅ Terraform state matches AWS reality


