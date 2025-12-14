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

### Grant administrative (sudo) privileges
bash
sudo usermod -aG sudo student

### Verify sudo access
groups student

### SSH Key-Based Authentication Configuration
Key-based authentication was implemented to replace password-based login, significantly improving SSH security.

### Generate SSH key pair on the workstation
ssh-keygen -t ed25519

### Copy public key to the server
ssh-copy-id student@192.168.56.102

### Test SSH login using key authentication
ssh student@192.168.56.102

### SSH Hardening
The SSH daemon configuration was hardened to reduce the attack surface.

### Edit SSH configuration file
sudo nano /etc/ssh/sshd_config

### Applied configuration changes
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes

### Restart SSH service
sudo systemctl restart ssh

### Firewall Configuration (UFW)

A firewall was configured to restrict access and protect the server.

### Enable UFW
sudo ufw enable

### Allow SSH from the workstation only
sudo ufw allow from 192.168.56.1 to any port 22

### Deny all other incoming connections
sudo ufw default deny incoming

### Verify firewall status
sudo ufw status verbose

### Remote Administration Evidence
All configuration tasks were executed remotely via SSH from the Windows workstation. Successful connections using key-based authentication confirmed that the SSH hardening and firewall rules were correctly applied.

### Weekly Reflection
This week reinforced the importance of secure access control and least-privilege administration. Disabling root login, enforcing SSH key-based authentication, and restricting firewall access significantly reduced the system’s attack surface. Performing all configuration tasks remotely strengthened my command-line proficiency and reflected industry-standard server administration practices.
