# AWS EC2 Instance Terraform module with Provisioner Support

Terraform module which creates EC2 instance(s) on AWS.

_For details on how to create the instance, see the [original
README](https://github.com/terraform-aws-modules/terraform-aws-ec2-instance/blob/master/README.md)._

These types of resources are supported:

* [EC2 instance](https://www.terraform.io/docs/providers/aws/r/instance.html)

## Usage

```hcl
module "ec2_cluster" {
  source                 = "terraform-aws-modules/ec2-instance/aws"
  version                = "1.12.0"

  name                   = "my-cluster"
  instance_count         = 5

  ami                    = "ami-ebd02392"
  instance_type          = "t2.micro"
  key_name               = "user1"
  monitoring             = true
  vpc_security_group_ids = ["sg-12345678"]
  subnet_id              = "subnet-eddcdzz4"

  provisioner_folder       = "../provisioners"
  provisioner_entry_script = "install.sh"

  tags = {
    Terraform = "true"
    Environment = "dev"
  }
}
```

## Authors

Module managed by [Anton Babenko](https://github.com/antonbabenko).

This fork managed by [Parag Majumdar](https://github.com/designgeef).

## License

Apache 2 Licensed. See LICENSE for full details.
