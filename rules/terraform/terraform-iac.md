---
name: Terraform Infrastructure as Code
globs: "**/*.tf"
alwaysApply: false
description: Best practices for Terraform infrastructure management
---

You are an expert in Terraform, Infrastructure as Code, and cloud architecture.

## Project Structure

- Organize code into modules for reusability
- Use consistent file naming (main.tf, variables.tf, outputs.tf)
- Separate environments using workspaces or directories
- Keep provider configurations in versions.tf
- Use remote state with state locking

## Resource Naming

- Use consistent naming conventions with prefixes
- Include environment in resource names
- Use tags for resource organization
- Follow cloud provider naming restrictions
- Document naming patterns in README

## State Management

- Always use remote state (S3, Azure Storage, etc.)
- Enable state locking to prevent conflicts
- Implement state backup strategies
- Use terraform import for existing resources
- Never commit state files to version control

## Security Best Practices

- Use variables for sensitive values
- Store secrets in secure backends (Vault, AWS Secrets Manager)
- Implement least privilege IAM policies
- Use encryption for state files
- Audit terraform plans before applying

## Code Quality

- Format code with terraform fmt
- Validate configurations with terraform validate
- Use terraform-docs for module documentation
- Implement pre-commit hooks for linting
- Write reusable modules with clear interfaces

## Module Design

```hcl
# Good module structure
module "vpc" {
  source  = "./modules/vpc"
  version = "1.0.0"
  
  name        = var.vpc_name
  cidr_block  = var.vpc_cidr
  environment = var.environment
  
  tags = merge(local.common_tags, {
    Module = "vpc"
  })
}
```

## Best Practices

- Use data sources instead of hardcoding values
- Implement proper dependency management
- Plan infrastructure changes in staging first
- Document module inputs and outputs
- Use conditional resources sparingly