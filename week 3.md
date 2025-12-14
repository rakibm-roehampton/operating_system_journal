# Week 3 – Application Selection for Performance Testing

**Student Name:** Mehedi Hasan Rakib  
**Student ID:** A00022820  
**Module:** CMPN202 – Operating Systems  

---

## Introduction

This week focuses on selecting representative applications to evaluate operating system performance under different workload types. Each application is chosen to place stress on specific system resources such as CPU, memory, disk I/O, and network bandwidth. This structured selection ensures that performance testing in later weeks is meaningful, measurable, and aligned with real-world server workloads.

---

## Application Selection Matrix

| Workload Type | Application | Justification |
|---------------|------------|---------------|
| CPU-intensive | stress-ng | Generates controlled CPU load to analyse processor utilisation, scheduling behaviour, and system stability under stress conditions. |
| Memory-intensive | stress-ng (vm test) | Allocates and stresses virtual memory to evaluate RAM usage, swapping behaviour, and memory pressure handling. |
| Disk I/O-intensive | fio | Industry-standard benchmarking tool used to measure disk read/write throughput, latency, and I/O performance. |
| Network-intensive | iperf3 | Measures network bandwidth and latency between systems, suitable for client-server testing over SSH. |
| Server application | nginx | Lightweight web server used to analyse service response time, process management, and concurrent connection handling. |

---

## Installation Documentation (SSH-based)

All selected applications were installed on the Ubuntu Server using secure SSH access from the Windows workstation. Installation was performed using the Advanced Package Tool (APT) to ensure consistency and reproducibility.

---

## Update System Packages and Install Applications

```bash
sudo apt update
sudo apt install stress-ng -y
sudo apt install fio -y

