Terraform module to provision an EC2 instance that is running Apache. 

Not inetended for production use. It is used to show case how to create a public custom module on Terraform Registry. 

```hcl

terraform {
  
}

provider "aws" {
  region = "us-east-1"
}

module "apache" {
  source = ".//terraform-aws-apache-example"
  vpc_id = "vpc-00000000000"
  my_ip_with_cidr = "MY_OWN_IP_ADDRESS"
  public_key = "ssh-rsa AAAAB....."
  instance_type = "t2.micro"
  server_name = "Apache Example Server"
}

output "public_ip" {
  value = module.apache.public_ip
}

```