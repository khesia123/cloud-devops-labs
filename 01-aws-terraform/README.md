# 01 — AWS EC2 with Terraform and Ansible

## Objective

Provision an AWS EC2 instance with **Terraform** and use **Ansible** to configure a simple web server for a hands-on infrastructure automation lab.

This project documents practical work while developing Cloud and DevOps skills. It is a learning lab, not a production deployment.

## Technologies

- AWS EC2
- Terraform
- Ansible
- Linux / Ubuntu
- Git and GitHub
- AWS CLI

## Environment

| Item | Configuration |
|---|---|
| AWS Region | `us-east-1` |
| EC2 instance type | `t3.micro` |
| Terraform AWS provider | `hashicorp/aws` (`~> 4.16`) |
| EC2 key pair name | `iac-alura` |

The private SSH key is kept locally and is not part of this repository.

## Project structure

```text
01-aws-terraform/
├── .gitignore
├── .terraform.lock.hcl
├── main.tf
├── hosts.yml
├── playbook.yml
└── README.md
```

## What this lab covers

1. Configure the AWS provider in Terraform.
2. Define an EC2 instance as infrastructure as code.
3. Initialize, validate, plan, and apply the Terraform configuration.
4. Use an Ansible inventory to identify the EC2 host.
5. Run an Ansible playbook that copies a test `index.html` page to the instance.
6. Start a lightweight BusyBox HTTP server on port `8080`.
7. Remove the test infrastructure with Terraform when it is no longer needed.

## Run the lab

Run Terraform from this directory:

```bash
terraform init
terraform fmt
terraform validate
terraform plan
terraform apply
```

After the EC2 instance is available, update the inventory on your local machine with its current public IP:

```ini
[terraform-ansible]
YOUR_SERVER_IP
```

Then run the Ansible playbook:

```bash
ansible-playbook -i hosts.yml playbook.yml
```

When the lab is finished, remove the resources created by this configuration:

```bash
terraform destroy
```

Review the Terraform plan before applying or destroying resources. AWS usage can incur charges; check the current pricing and your account's Free Tier eligibility before running the lab.

## Security and repository hygiene

The repository must not contain:

- Private SSH keys (`.pem`, `.key`)
- AWS credentials, passwords, or access tokens
- Real public IP addresses in the inventory
- Terraform state files (`*.tfstate*`)
- Local Terraform working directories (`.terraform/`)
- Local secret variable files (`*.tfvars`, `.env*`)

Use your local AWS CLI credential configuration or another approved credential mechanism. Keep the inventory's `YOUR_SERVER_IP` placeholder in Git and replace it only in your local working copy.

## Current status

**In progress.** The lab structure and initial Git commit are prepared locally. The source files and execution evidence still need to be published and reviewed in this repository before the lab can be marked complete.

## Author

**Khesia Nunes** — IT Infrastructure professional developing practical skills in Cloud and DevOps.

- [GitHub profile](https://github.com/khesia123)
- [LinkedIn](https://www.linkedin.com/in/khesia-nunes-992982190/)
