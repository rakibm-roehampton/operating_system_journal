# Week 5 – Advanced Security and Monitoring Infrastructure

**Student Name:** Mehedi Hasan Rakib  
**Student ID:** A00022820  
**Module:** CMPN202 – Operating Systems  

---

## Introduction

This week focuses on implementing advanced security mechanisms and developing monitoring capabilities on the Ubuntu Server. Mandatory access control, automated security updates, intrusion prevention, and custom verification and monitoring scripts were deployed to strengthen the overall system security. All configurations were performed remotely via SSH from the workstation, following professional server administration practices.

---

## Mandatory Access Control (AppArmor)

Ubuntu Server uses AppArmor to enforce mandatory access control by restricting how applications interact with system resources.

### Verify AppArmor status
bash
sudo aa-status#

## Ensure AppArmor is enabled and running
sudo systemctl enable apparmor
sudo systemctl start apparmor

## Check loaded AppArmor profiles
sudo aa-status --profiles

AppArmor reduces the impact of compromised applications by enforcing least-privilege execution policies.

## Automatic Security Updates

Automatic security updates were configured to ensure that critical security patches are applied without manual intervention.

## Install unattended-upgrades
sudo apt install unattended-upgrades -y

## Configure automatic updates
sudo dpkg-reconfigure --priority=low unattended-upgrades

## Verify unattended-upgrades service
systemctl status unattended-upgrades

This configuration reduces exposure to known vulnerabilities by ensuring timely patching.

## Intrusion Detection and Prevention (Fail2Ban)

Fail2Ban was deployed to protect the server against brute-force attacks by monitoring authentication logs and banning malicious IP addresses.

## Install fail2ban
sudo apt install fail2ban -y

## Enable and start fail2ban
sudo systemctl enable fail2ban
sudo systemctl start fail2ban

## Verify fail2ban status
sudo fail2ban-client status


Fail2Ban strengthens SSH security by automatically blocking repeated failed login attempts.

## Security Baseline Verification Script

A security baseline verification script was created to confirm that key security controls are correctly configured.

## Create the security baseline script
nano security-baseline.sh

## Script content
#!/bin/bash

echo "Checking SSH root login configuration:"
grep "^PermitRootLogin no" /etc/ssh/sshd_config

echo "Checking password authentication is disabled:"
grep "^PasswordAuthentication no" /etc/ssh/sshd_config

echo "Checking firewall status:"
sudo ufw status verbose

echo "Checking AppArmor status:"
sudo aa-status

echo "Checking fail2ban status:"
sudo systemctl status fail2ban --no-pager

## Make the script executable
chmod +x security-baseline.sh


This script provides a repeatable method for verifying security configurations and supports systematic auditing.

## Remote Monitoring Script

A remote monitoring script was developed on the workstation to collect system performance metrics from the server via SSH.

## Create monitoring script on workstation
nano monitor-server.sh

## Script content
#!/bin/bash

SERVER_IP="192.168.56.102"
USER="student"

ssh ${USER}@${SERVER_IP} << EOF
echo "CPU and Memory Usage:"
top -b -n 1 | head -20

echo "Memory Usage:"
free -h

echo "Disk Usage:"
df -h

echo "Network Interfaces:"
ip addr
EOF

## Make the script executable
chmod +x monitor-server.sh


This script enables automated, repeatable monitoring without requiring direct server console access.

## Weekly Reflection

This week demonstrated the importance of layered security in operating system design. Implementing AppArmor, automated security updates, and fail2ban significantly improved the server’s resilience against attacks. Developing verification and monitoring scripts strengthened my understanding of automation and reinforced industry-standard system administration practices.

