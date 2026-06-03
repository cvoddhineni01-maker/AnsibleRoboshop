# Roboshop Ansible Automation

## Overview

This repository contains Ansible playbooks and inventory files for deploying the Roboshop 3-tier architecture on AWS. It includes infrastructure provisioning and application orchestration for a sample microservices-based e-commerce platform.

## Repository Structure

- `01_ec2-r53.yaml` - Provision EC2 instances and Route 53 records.
- `catalogue.yaml` - Deploy the catalogue service.
- `mongo.repo` - YUM repository configuration for MongoDB.
- `mongodb.yaml` - Deploy MongoDB service.
- `mysql.yaml` - Deploy MySQL service.
- `rabbitmq.repo` - YUM repository configuration for RabbitMQ.
- `rabbitmq.yaml` - Deploy RabbitMQ service.
- `redis.yaml` - Deploy Redis service.
- `test.yaml` - Test connectivity or service deployment.
- `inventory.ini` - Ansible inventory file for target hosts.
- `readme.md` - This project documentation.

## Prerequisites

1. Install Ansible:

```bash
sudo dnf install ansible -y
```

2. Install Python AWS dependencies:

```bash
pip3 install boto3 botocore
```

3. Configure AWS CLI credentials:

```bash
aws configure
```

Provide your AWS Access Key ID, Secret Access Key, default region, and output format.

## Usage

Run the main Ansible playbook with the inventory file:

```bash
ansible-playbook -i inventory.ini 01_ec2-r53.yaml
```

> Adjust the playbook name or inventory file as needed for individual service deployments.

## Common Tasks

- Provision infrastructure and DNS:
  - `ansible-playbook -i inventory.ini 01_ec2-r53.yaml`
- Deploy MongoDB:
  - `ansible-playbook -i inventory.ini mongodb.yaml`
- Deploy MySQL:
  - `ansible-playbook -i inventory.ini mysql.yaml`
- Deploy RabbitMQ:
  - `ansible-playbook -i inventory.ini rabbitmq.yaml`
- Deploy Redis:
  - `ansible-playbook -i inventory.ini redis.yaml`
- Deploy Catalogue service:
  - `ansible-playbook -i inventory.ini catalogue.yaml`

## Notes

- Ensure your `inventory.ini` file contains the correct host IPs or hostnames.
- Verify SSH access to target servers from the machine running Ansible.
- Update repository and playbook variables for your AWS environment before deployment.

## Architecture

This project targets a 3-tier ecommerce architecture, typically including:

- Web/application services
- Database services (MySQL / MongoDB)
- Messaging/cache services (RabbitMQ / Redis)

## Support

If you need to customize the deployment, edit the corresponding playbook and inventory entries. For AWS-specific configuration, update the AWS credential setup and region settings.

---

![Roboshop Architecture](roboshop.jpg)
