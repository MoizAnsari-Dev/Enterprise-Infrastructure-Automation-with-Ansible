# Enterprise Infrastructure Automation with Ansible  
### Managing 100+ AWS EC2 Instances at Scale

![Status](https://img.shields.io/badge/Project-Production%20Ready-brightgreen)
![Ansible](https://img.shields.io/badge/Automation-Ansible-red)
![AWS](https://img.shields.io/badge/Cloud-AWS-orange)
![EC2](https://img.shields.io/badge/Compute-EC2-yellow)
![Linux](https://img.shields.io/badge/OS-Linux-blue)
![Prometheus](https://img.shields.io/badge/Monitoring-Prometheus-orange)
![Grafana](https://img.shields.io/badge/Visualization-Grafana-yellow)

---

## Overview

This project demonstrates enterprise-grade infrastructure automation and monitoring using **Ansible**
to manage and secure **100+ AWS EC2 instances**.

Key highlights:

- Dynamic AWS EC2 Inventory
- Role-based architecture
- SSH hardening
- Security baseline enforcement
- Parallel execution for scalability
- Prometheus
- Grafana
- Production-ready configuration structure

---

## Architecture

Ansible Control Node securely connects to multiple EC2 instances using SSH (key-based authentication) 
and applies configuration consistently across all environments.

---

## Tech Stack

| Technology | Purpose |
|------------|----------|
| Ansible | Configuration Management |
| AWS EC2 | Scalable Cloud Infrastructure |
| amazon.aws Collection | Dynamic Inventory |
| Linux | Target OS |
| SSH | Secure Access |

---

## Project Structure
```
ansible-100-servers/
│
├── inventory/
│   └── aws_ec2.yml
│
├── group_vars/
│   └── all.yml
│
├── roles/
│   ├── common/
│   ├── ssh_hardening/
│   └── security/
│
├── site.yml
├── ansible.cfg
└── README.md
```
---

## Core Features

### Dynamic AWS Inventory

Automatically discovers running EC2 instances using:
```
plugin: amazon.aws.aws_ec2  
regions:  
  - us-east-1  
filters:  
  instance-state-name: running  
```
---

### SSH Hardening

- Root login disabled  
- Password authentication disabled  
- Enforced key-based authentication  

---

### Parallel Execution

Configured in ansible.cfg:
```
[defaults]  
forks = 50  
host_key_checking = False  
```
---

## How to Run

###  Install Dependencies
```
pip install boto3 botocore  
ansible-galaxy collection install amazon.aws  
```
---

###  Configure AWS Credentials
```
aws configure  
```
Or attach IAM role (recommended in production).

---

###  Configure SSH Key
```
mv mykey.pem ~/.ssh/  
chmod 400 ~/.ssh/mykey.pem  
```
Update ansible.cfg:
```
private_key_file = ~/.ssh/mykey.pem  
```
---

###  Validate Inventory
```
ansible-inventory -i inventory/aws_ec2.yml --graph  
```
<img width="705" height="312" alt="image" src="https://github.com/user-attachments/assets/0c3da76c-f65f-4570-b174-ac8f75531e4f" />

---

###  Execute Playbook
```
ansible-playbook site.yml  
```
<img width="1263" height="140" alt="image" src="https://github.com/user-attachments/assets/34f48e32-b0e3-4a36-a3c7-c1137065ffec" />

---

## Security Best Practices

- Key-based SSH authentication only  
- No hardcoded credentials  
- IAM role-based access recommended  
- Role-based configuration management  

---
## Monitoring Stack
### Prometheus and Grafana
<img width="1866" height="876" alt="image" src="https://github.com/user-attachments/assets/88da1d5b-95a8-4124-8c79-e5c86bb250a0" />
