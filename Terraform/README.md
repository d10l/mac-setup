# Terraform

## Installation

[Install](https://learn.hashicorp.com/terraform/getting-started/install.html) locally and then [setup for your peferred cloud (e.g. AWS)](https://learn.hashicorp.com/terraform/getting-started/build).

```sh
brew install terraform
```

## Usage

[Configure](https://learn.hashicorp.com/terraform/getting-started/build) the provider you need (e.g. AWS). 

Initialize the repository

```sh
terraform init
```

Apply changes

```sh
terraform apply
```

Change Infrastructure: https://learn.hashicorp.com/terraform/getting-started/change

Destroy Infrastructure: https://learn.hashicorp.com/terraform/getting-started/destroy

```sh
terraform destroy
```

Dependencies between components: https://learn.hashicorp.com/terraform/getting-started/dependencies

Input Variables: https://learn.hashicorp.com/terraform/getting-started/variables

Output Variables: https://learn.hashicorp.com/terraform/getting-started/outputs

Store State remotely (s3): https://learn.hashicorp.com/terraform/getting-started/remote



Developer: https://learn.hashicorp.com/terraform/?track=development#development
Operations: https://learn.hashicorp.com/terraform/?track=operations#operations


