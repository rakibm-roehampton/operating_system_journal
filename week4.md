# Week 4 – Initial System Configuration & Security Implementation

**Student Name:** Mehedi Hasan Rakib  
**Student ID:** A00022820  
**Module:** CMPN202 – Operating Systems  

---

## Introduction

This week focuses on deploying the Ubuntu Server and implementing foundational security controls. All system administration tasks were performed remotely via SSH from the Windows workstation, enforcing command-line proficiency and professional remote administration practices. The objective is to secure access, restrict privileges, and protect the server from unauthorised access.

---

## User Management and Privilege Configuration

To follow the principle of least privilege, a non-root administrative user was created. Direct root login was avoided to reduce security risk.

### Create a non-root administrative user
bash
sudo adduser student
sudo usermod -aG sudo student
groups student
ssh-keygen -t ed25519
ssh-copy-id student@192.168.56.102
ssh student@192.168.56.102
sudo nano /etc/ssh/sshd_config
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
sudo systemctl restart ssh
sudo ufw enable
sudo ufw allow from 192.168.56.1 to any port 22
sudo ufw default deny incoming
sudo ufw status verbose
