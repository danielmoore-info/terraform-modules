# Mailcow Terraform Module

Used for deploying Mailcow into AWS.

Includes:
- Seperate VPC for the services
- Mail Server 
- Mail Security Group
- DNS records for a given domain

## Example Usage

Create a new folder and create a main.tf file with the following contents

```text
# main.tf
provider "aws" {
  profile = "default"
  region = "ap-southeast-2"
}

module "mailcow" {
  source = "github.com/danielmoore-info/terraform-modules//aws/services/mailcow"
  public_key = ""
  domain = ""
}
```

You should then run the provided ansible playbook against the new mail server (make sure to add the host to your /etc/ansible/hosts file).

```bash
ansible-playbook --private-key /path/to/key -e "mailcow_hostname=example.com" .terraform/modules/mailcow/aws/services/mailcow/configuration/mailcow-ansible.yml
```
