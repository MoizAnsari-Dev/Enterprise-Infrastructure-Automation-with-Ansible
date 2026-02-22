# 🚀 Enterprise Infrastructure Automation with Ansible  
### Managing 100+ AWS EC2 Instances at Scale

![Ansible](https://img.shields.io/badge/Automation-Ansible-red)
![AWS](https://img.shields.io/badge/Cloud-AWS-orange)
![EC2](https://img.shields.io/badge/Compute-EC2-yellow)
![Linux](https://img.shields.io/badge/OS-Linux-blue)
![Status](https://img.shields.io/badge/Project-Production%20Ready-brightgreen)

---

## 📌 Overview

This project demonstrates enterprise-grade infrastructure automation using **Ansible**
to manage and secure **100+ AWS EC2 instances**.

Key highlights:

- Dynamic AWS EC2 Inventory
- Role-based architecture
- SSH hardening
- Security baseline enforcement
- Parallel execution for scalability
- Production-ready configuration structure

---

## 🏗️ Architecture

Ansible Control Node securely connects to multiple EC2 instances using SSH (key-based authentication) 
and applies configuration consistently across all environments.

---

## 🛠️ Tech Stack

| Technology | Purpose |
|------------|----------|
| Ansible | Configuration Management |
| AWS EC2 | Scalable Cloud Infrastructure |
| amazon.aws Collection | Dynamic Inventory |
| Linux | Target OS |
| SSH | Secure Access |

---

## 📂 Project Structure

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

---

## ⚙️ Core Features

### ✅ Dynamic AWS Inventory

Automatically discovers running EC2 instances using:

plugin: amazon.aws.aws_ec2  
regions:  
  - us-east-1  
filters:  
  instance-state-name: running  

---

### ✅ SSH Hardening

- Root login disabled  
- Password authentication disabled  
- Enforced key-based authentication  

---

### ✅ Parallel Execution

Configured in ansible.cfg:

[defaults]  
forks = 50  
host_key_checking = False  

---

## 🚀 How to Run

### 1️⃣ Install Dependencies

pip install boto3 botocore  
ansible-galaxy collection install amazon.aws  

---

### 2️⃣ Configure AWS Credentials

aws configure  

Or attach IAM role (recommended in production).

---

### 3️⃣ Configure SSH Key

mv mykey.pem ~/.ssh/  
chmod 400 ~/.ssh/mykey.pem  

Update ansible.cfg:

private_key_file = ~/.ssh/mykey.pem  

---

### 4️⃣ Validate Inventory

ansible-inventory -i inventory/aws_ec2.yml --graph  

---

### 5️⃣ Execute Playbook

ansible-playbook site.yml  

---

## 🔐 Security Best Practices

- Key-based SSH authentication only  
- No hardcoded credentials  
- IAM role-based access recommended  
- Role-based configuration management  

---

## 🎯 Resume-Ready Description

Engineered enterprise-grade infrastructure automation for 100+ AWS EC2 instances using Ansible with dynamic inventory, implemented SSH hardening and security baselines using role-based architecture, and optimized deployment efficiency through parallel execution.

---

## 👨‍💻 Author

Moiz Ansari  
DevOps | Cloud | Infrastructure Automation
