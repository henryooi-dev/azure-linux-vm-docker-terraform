# Azure Linux VM with Docker - Terraform

This repository contains Terraform scripts to provision a Linux Virtual Machine on Azure with Docker installed. It includes configuration for networking, security groups, a public IP, and SSH access. The setup supports host machines running Windows, Linux, or macOS.

## Features

- Create an Azure Resource Group
- Create Virtual Network (VNet) and Subnet
- Create Network Security Group with inbound rules
- Assign NSG to Subnet
- Create Public IP
- Create Network Interface
- Deploy a Linux VM with Docker installed
- SSH automation for Windows, Linux, and macOS hosts
- Output public IP of the VM

## Prerequisites

- Azure account
- [Azure CLI installed](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-windows?view=azure-cli-latest&pivots=winget)
- VS Code with Terraform extension
- SSH key generated for VM access

## Setup

1. Clone this repository:
   ```bash
   git clone https://github.com/<your-username>/azure-linux-vm-docker-terraform.git
   cd azure-linux-vm-docker-terraform
   ```
2. Login to Azure CLI:
   ```bash
   az login
   az account show
   ```
3. Initialize Terraform:
   ```bash
   terraform init
   ```
4. Plan your deployment:
   ```bash
   terraform plan
   ```
5. Apply the Terraform scripts:
   ```bash
   terraform apply
   # Or without confirmation prompt
   terraform apply -auto-approve
   ```
6. Access your VM via SSH:
   ```bash
   ssh -i ~/.ssh/mtcazurekey azureuser@<public-ip>
   ```
   
File Structure
- main.tf - Main Terraform configuration
- variables.tf - Terraform variables
- terraform.tfvars - Default variables for host OS
- osx.tfvars - Variables for macOS host
- customdata.tpl - Cloud-init script to install Docker
- windows-ssh-script.tpl - PowerShell script to configure SSH on Windows

Terraform Commands Reference
- terraform fmt - Formats your Terraform files
- terraform init - Initializes Terraform
- terraform plan - Shows deployment plan
- terraform apply - Deploys resources
- terraform apply -auto-approve - Deploy without confirmation
- terraform apply -replace <resource> - Force recreate resource
- terraform state list - List resources in state
- terraform state show <resource> - Show resource attributes
- terraform output - Show output variables
- terraform plan -destroy - Plan to destroy all resources
- terraform apply -destroy - Destroy all deployed resources

SSH Commands Reference
- ssh-keygen -t rsa - Generate SSH key
- ssh-keygen -R <ip_address> - Remove saved SSH fingerprint
- ls ~/.ssh - List SSH keys
- ssh -i ~/.ssh/<key> <user>@<public-ip> - Connect to VM
