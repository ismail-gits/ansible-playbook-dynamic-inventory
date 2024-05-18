# Ansible Playbook with Dynamic Inventory

This repository contains an Ansible playbook and associated configurations for deploying Docker containers on EC2 instances provisioned using Terraform.

## Directory Structure

- **terraform-ec2**: Terraform configuration directory.
    - **main.tf**: Terraform configuration file for provisioning VPC, subnets, security groups, and EC2 instances.
    - **terraform.tfvars**: Terraform variables file containing configuration parameters such as VPC CIDR block, subnet CIDR block, etc.
- **ansible.cfg**: Ansible configuration file specifying settings like inventory and remote user.
- **deploy-docker-vars.yaml**: Ansible variables file for Docker deployment containing sensitive information.
- **deploy-docker.yaml**: Ansible playbook for deploying Docker containers on EC2 instances.
- **docker-compose.yaml**: Docker Compose file defining services and containers.
- **inventory_aws_ec2.yaml**: Ansible dynamic inventory file for AWS EC2 instances.
- **manual-installation-docker.sh**: Shell script for manual Docker installation.

## Usage

1. **Terraform Configuration**:
   - Navigate to the `terraform-ec2` directory.
   - Modify the `terraform.tfvars` file with desired configurations.
   - Execute `terraform init` and `terraform apply` to provision EC2 instances on AWS.

2. **Ansible Configuration**:
   - Update `ansible.cfg` with necessary settings.
   - Ensure that the dynamic inventory script `inventory_aws_ec2.yaml` is correctly configured.
   - Update `deploy-docker-vars.yaml` with Docker registry credentials.

3. **Deploy Docker Containers**:
   - Run the Ansible playbook `deploy-docker.yaml` to deploy Docker containers on EC2 instances.
   - Ensure that the Docker Compose file `docker-compose.yaml` is correctly configured for your application.

4. **Manual Installation (Optional)**:
   - If needed, you can use `manual-installation-docker.sh` for manual Docker installation on servers.

## Notes
- This setup assumes Terraform is used for infrastructure provisioning and Ansible for configuration management.
- Ensure proper access and secret keys are set up for Terraform to interact with AWS.
- Adjust security configurations, such as SSH key pairs and security group rules, according to your requirements.
- Docker registry credentials should be handled securely, possibly using Ansible Vault for sensitive data.
- Review and modify shell scripts (`manual-installation-docker.sh`) before executing them in production environments.