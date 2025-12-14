# Week 3 – Application Selection for Performance Testing

**Student Name:** Mehedi Hasan Rakib  
**Student ID:** A00022820  
**Module:** CMPN202 – Operating Systems  

---

## Introduction

This week focuses on selecting appropriate applications to evaluate operating system performance under different workload types. Each application is chosen to stress a specific system resource, allowing meaningful performance analysis and comparison in later weeks.

---

## Application Selection Matrix

| Workload Type | Application | Justification |
|---------------|------------|---------------|
| CPU-intensive | stress-ng | Generates controlled CPU load to analyse processor utilisation and scheduling behaviour. |
| Memory-intensive | stress-ng (vm test) | Stresses memory allocation to observe RAM usage and swapping behaviour. |
| Disk I/O-intensive | fio | Benchmarks disk read/write throughput and I/O latency. |
| Network-intensive | iperf3 | Measures network bandwidth and latency in client-server mode. |
| Server application | nginx | Simulates a real-world server workload with concurrent connections. |

---

## Installation Documentation (SSH-based)

All applications were installed on the Ubuntu Server using secure SSH access from the Windows workstation.

---

## Update System Packages and Install Applications

bash
sudo apt update
sudo apt install stress-ng -y
sudo apt install fio -y
sudo apt install iperf3 -y
sudo apt install nginx -y

---

## Expected Resource Usage Profiles

### CPU-intensive workload
- High CPU utilisation across all available cores  
- Increased scheduler activity and context switching  

### Memory-intensive workload
- Rapid allocation and deallocation of memory  
- Increased swap usage if RAM limits are exceeded  

### Disk I/O-intensive workload
- High read/write operations  
- Increased I/O wait times during peak usage  

### Network-intensive workload
- High bandwidth usage  
- Observable latency under load  

### Server application workload
- Moderate CPU and memory usage  
- Multiple worker processes handling concurrent connections  

---

## Monitoring Strategy

The following command-line tools will be used in later weeks to monitor system performance:

- `top` / `htop` – CPU and memory usage  
- `free -h` – Memory utilisation  
- `vmstat` – System activity  
- `iostat` – Disk I/O performance  
- `ss` and `ip` – Network statistics  

---

## Weekly Reflection

This week improved my understanding of how different workloads stress specific operating system resources. Selecting appropriate applications ensures that performance testing is structured, measurable, and relevant to real-world server environments.
