# Week 7 – Security Audit and System Evaluation

**Student Name:** Mehedi Hasan Rakib  
**Student ID:** A00022820  
**Module:** CMPN202 – Operating Systems  

---

## Introduction

This week focuses on conducting a comprehensive security audit and evaluating the overall system configuration of the Ubuntu Server. Industry-standard security assessment tools were used to identify vulnerabilities, review running services, and assess remaining risks. The results were analysed to understand the trade-offs between security, performance, and usability in operating system design.

---

## Security Audit with Lynis

Lynis was used to perform an in-depth security audit of the server. It evaluates system hardening, service configuration, and potential vulnerabilities.

### Install Lynis
bash
sudo apt install lynis -y

## Run Lynis audit
sudo lynis audit system

## Lynis Results Summary

Initial Lynis security score identified several hardening opportunities

Warnings related to SSH configuration, firewall rules, and system services

Suggestions were reviewed and applied where appropriate

After implementing recommendations from previous weeks (SSH hardening, UFW, AppArmor, fail2ban), the overall Lynis score improved, demonstrating a stronger security posture.

## Network Security Assessment (nmap)

A controlled network scan was performed within the isolated VirtualBox network to identify open ports and exposed services.

## Run nmap scan (from workstation)
nmap -sS 192.168.56.102

## Scan Results

| Port | Service | Status | Justification |
|------|---------|--------|---------------|
| 22   | SSH     | Open   | Required for secure remote administration |
| 80   | HTTP    | Open   | Required for Nginx web server testing |
| All others | - | Closed | Reduced attack surface |

The scan confirmed that only essential services were exposed.

## SSH Security Verification

SSH security settings were verified to ensure compliance with best practices.

## Verified configurations

Root login disabled

Password authentication disabled

Key-based authentication enforced

Access restricted via firewall rules

These controls significantly reduce the risk of brute-force and unauthorised access.

## Service Audit and Justification

All running services were reviewed to ensure they were necessary and securely configured.

## List active services
systemctl list-units --type=service --state=running

## Service Inventory

The following table lists all active and relevant services identified on the Ubuntu Server VM during the security audit. Each service is evaluated based on necessity, exposure, and security justification.

| Service Name | Port | Protocol | Status | Purpose | Security Justification |
|-------------|------|----------|--------|---------|------------------------|
| ssh | 22 | TCP | Enabled | Remote system administration | Essential for secure server management using key-based authentication |
| nginx | 80 | TCP | Enabled | Web server testing | Required for performance and service availability testing |
| systemd-resolved | - | - | Enabled | DNS resolution | Core system service required for networking |
| cron | - | - | Enabled | Scheduled tasks | Required for system maintenance jobs |
| ufw | - | - | Enabled | Firewall management | Enforces inbound and outbound access control |
| fail2ban | - | - | Enabled | Intrusion prevention | Protects against brute-force SSH attacks |

All non-essential services were disabled or not installed to minimise the system’s attack surface.

## Access Control Verification

Mandatory access control and firewall configurations were verified.

## AppArmor status
sudo aa-status

## Firewall status
sudo ufw status verbose

Both controls were active and enforcing the intended security policies.

## Remaining Risk Assessment

Despite strong security controls, some residual risks remain:

Zero-day vulnerabilities in installed software

Insider threats through authorised user access

Denial-of-service attacks targeting exposed services

These risks are mitigated through:

Regular updates

Minimal service exposure

Monitoring and logging

## Critical System Evaluation

This coursework demonstrated the trade-offs inherent in operating system design. Strong security controls can slightly increase system overhead, but the impact on performance was minimal compared to the security benefits gained. The system configuration reflects a balanced approach between performance efficiency, usability, and security hardening.

## Weekly Reflection

This final week consolidated my understanding of operating system security and evaluation. Performing audits, analysing scan results, and justifying system configurations reinforced the importance of continuous assessment and informed decision-making. The coursework demonstrated how layered security controls and careful configuration contribute to a robust and professionally managed operating system.


