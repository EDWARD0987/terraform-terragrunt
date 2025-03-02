# Overview

A repo to explain the purpose of Terragrunt. The wordpress example is taken from: https://github.com/devbhusal/terraform-ec2-RDS-wordpress.
This is also a good reference for Terragrunt: https://blog.gruntwork.io/terragrunt-how-to-keep-your-terraform-code-dry-and-maintainable-f61ae06959d8.

## Instructions

### First Try Terraform 

In the `Terraform_Only/environments/dev` folder create a private/public key pair with an empty passphrase:

```bash
ssh-keygen -f mykey-pair
sudo chmod 400 mykey-pair
```

In order to create a remote backend to store Terraform state files, you will need to create an S3 bucket and a Dynamo DB table. 
Run Terraform commands

```bash
terraform init
terraform plan
terraform apply
```

### Finally Try Terragrunt

In the `Terragrunt/environments/dev` folder run the following command to create a private/public key pair with an empty passphrase:

```bash
ssh-keygen -f mykey-pair
sudo chmod 400 mykey-pair
```

Then run the following terragrunt commands:

```bash
terragrunt init
terragrunt plan
terragrunt apply
```

Terragrunt sets the AWS remote backend for you. It will create an S3 bucket and a Dynamo DB table.

## Clean Up

Terragrunt has a neat feature that allows you to run commands across multiple folders. In our case we will run the following command to destroy the dev and prod environments:

 $ terragrunt run-all destroy

