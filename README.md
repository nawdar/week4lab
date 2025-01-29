Terraform AWS Web Infrastructure Lab

Tgis project contains Terraform configurations to provision an AWS infrastructure with:
1.A VPC with a public subnet
2.An EC2 instance running Ubuntu 24.04
3.Security Groups allowing SSH (port 22) and HTTP (port 80)
4Cloud-Init script** to configure the EC2 instance with Nginx and Nmap

Generate SSH Key Pair

ssh-keygen -t rsa -b 4096 -f ~/.ssh/terraform-key -N 

#import the public key to AWS command:
aws ec2 import-key-pair --key-name "terraform-key" --public-key-material fileb://~/.ssh/terraform-key.pub


#Initialize Terraform command: 
terraform init

#Format Terraform Files:
terraform fmt

#Validate Configuration
terraform validate

#Plan the Infrastructure
terraform plan

#Apply Configuration to Deploy Resources
terraform apply -auto-approve

#Retrieve EC2 Public IP
terraform output instance_ip_addr

#SSH into EC2 Instance
ssh -i ~/.ssh/terraform-key web@<PUBLIC_IP>

#Destroying the Infrastructure
terraform destroy -auto-approve

refs:
https://registry.terraform.io/providers/hashicorp/aws/latest/docs
https://developer.hashicorp.com/terraform/language
https://docs.aws.amazon.com/cli/latest/reference/ec2/import-key-pair.html
https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/instance
https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/security_group
https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/vpc
https://developer.hashicorp.com/terraform/language/values/locals
https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/subnet
https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/internet_gateway
https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/route_table
https://cloudinit.readthedocs.io/en/latest/
https://developer.hashicorp.com/terraform/language/values/outputs
https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/vpc_security_group_egress_rule
https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/vpc_security_group_ingress_rule
https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/key_pair
https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/route_table_association
https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/route




