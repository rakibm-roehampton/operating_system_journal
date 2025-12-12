# Week 2 – Security Planning and Testing Methodology

**Student Name:** Mehedi Hasan Rakib  
**Student ID:** A00022820  
**Module:** CMPN202 – Operating Systems  

---

## Performance Testing Plan

The purpose of the performance testing plan is to establish a structured and repeatable methodology for analysing how the operating system behaves under different workloads. Performance data will be collected remotely from the Ubuntu Server using command-line tools accessed via SSH from the Windows 11 workstation.

Initial baseline measurements will be recorded while the system is idle. This baseline will be used as a reference point for later workload testing and optimisation analysis. The key system resources to be monitored include CPU usage, memory consumption, disk I/O activity, and network performance.

CPU performance will be analysed using tools such as `top` and `uptime` to observe processor utilisation and load averages. Memory usage will be monitored using `free -h` to assess available, used, and cached memory. Disk usage and storage behaviour will be examined using `df -h` and disk I/O tools to understand read and write activity. Network performance will be evaluated using tools such as `ip`, `ping`, and `ss` to measure connectivity, latency, and active connections.

All measurements will be collected in a consistent manner and recorded for comparison. This structured approach allows bottlenecks to be identified and provides quantitative evidence to support performance analysis in later stages of the coursework.

---

## Security Configuration Checklist

A security configuration checklist was designed to define a secure baseline for the Ubuntu Server before implementation. This checklist ensures that security controls are applied systematically and can be verified later.

SSH security will be strengthened by disabling password-based authentication and enforcing key-based authentication only. Direct root login over SSH will be disabled to reduce the risk of brute-force and privilege escalation attacks. SSH access will be restricted to the trusted workstation IP address.

A firewall will be configured using UFW (Uncomplicated Firewall) to deny all incoming connections by default. Only SSH traffic on port 22 from the workstation will be permitted. All unnecessary ports and services will remain blocked.

User privilege management will be implemented by creating a non-root administrative user with sudo privileges. Routine administrative tasks will be performed using this account rather than the root user.

Mandatory access control will be enforced using AppArmor to restrict application behaviour and limit the impact of potential exploits. Automatic security updates will be enabled to ensure timely patching of known vulnerabilities. Intrusion detection will be enhanced using fail2ban to monitor and block repeated failed login attempts.

---

## Threat Model

A threat model was developed to identify potential security risks to the Ubuntu Server and define appropriate mitigation strategies.

One significant threat is brute-force attacks targeting the SSH service. Attackers may attempt repeated login attempts to gain unauthorised access. This threat is mitigated by disabling password authentication, enforcing SSH key-based authentication, restricting SSH access by IP address, and deploying fail2ban to block repeated failed attempts.

Another potential threat is privilege escalation caused by misconfigured user permissions. Excessive privileges could allow an attacker to gain administrative control. This risk is mitigated by enforcing the principle of least privilege, disabling direct root login, and carefully managing sudo permissions.

A third threat involves exploitation of known vulnerabilities in outdated software packages. Unpatched systems may be vulnerable to publicly known exploits. This threat is mitigated by enabling automatic security updates and regularly auditing installed software.

These mitigation strategies collectively reduce the attack surface and establish a proactive security posture aligned with best practices.

---

## Weekly Reflection

This week focused on planning security and performance strategies prior to implementation. Developing a performance testing plan improved my understanding of how operating system resources should be measured and compared under different conditions. Creating the security checklist and threat model strengthened my awareness of layered security controls and proactive risk management. This planning phase provides a strong foundation for implementing and validating security mechanisms in the following weeks.
