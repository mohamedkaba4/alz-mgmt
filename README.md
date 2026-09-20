# Azure Landing Zone Management Platform

This repository contains the Terraform configuration used to deploy and manage the management layer of Azure Landing Zone.

The goal of this project is to form a governed Azure foundation with centralized management, policy, monitoring, and subscription organization using Infrastructure as Code.

## What This Repository Deploys

This repository is focused on the management and governance aspect of the Azure Landing Zone, including:

- Management group hierarchy
- Azure Policy assignments and governance controls
- Role-Based Access Control (RBAC) configuration
- Management subscription resources
- Log Analytics workspace
- Azure Automation resources
- Centralized monitoring and operational management
- Supporting platform configuration required by the Azure Landing Zone

## Architecture

The environment follows the Azure Landing Zone design principles and separates platform tasks across dedicated subscriptions and management groups.

The management subscription is used for centralized operational services like:

- Logging
- Monitoring
- Automation
- Governance
- Policy enforcement

Workload subscriptions are placed under the appropriate management groups so policies and access controls can be inherited consistently.

## Infrastructure as Code

Terraform is used to provision and manage the environment.

The deployment uses Azure Landing Zone accelerator components and Azure Verified Modules where appropriate, while environment-specific configuration is maintained in this repository.

Example workflow:

```bash
terraform init
terraform validate

terraform plan \
  -var-file="prod.tfvars"

terraform apply \
  -var-file="prod.tfvars"
