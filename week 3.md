# Week 3 – Application Selection for Performance Testing

**Student Name:** Mehedi Hasan Rakib  
**Student ID:** A00022820  
**Module:** CMPN202 – Operating Systems  


## Introduction

This week focuses on selecting representative applications to evaluate operating system performance under different workload types. The selected applications are designed to stress specific system resources such as CPU, memory, disk I/O, and network bandwidth. This structured approach ensures meaningful performance testing and prepares the system for detailed monitoring and optimisation in later weeks.


## Application Selection Matrix

| Workload Type | Application | Justification |
|---------------|------------|---------------|
| CPU-intensive | stress-ng | Used to generate controlled CPU load and analyse processor utilisation, scheduling behaviour, and system stability under stress. |
| Memory-intensive | stress-ng (vm test) | Allocates and stresses memory to observe RAM usage, swapping behaviour, and memory pressure handling. |
| Disk I/O-intensive | fio | Industry-standard benchmarking tool for measuring disk read/write throughput, latency, and I/O performance. |
| Network-intensive | iperf3 | Measures network bandwidth and latency, suitable for client-server testing over SSH. |
| Server application | nginx | Lightweight web server used to evaluate service response time, process handling, and concurrent connections. |


## Installation Documentation (SSH-based)

All applications were installed on the Ubuntu Server using secure SSH access from the Windows workstation.

## Update system packages

```bash
sudo apt update
sudo apt install stress-ng -y
sudo apt install fio -y
sudo apt install iperf3 -y
sudo apt install nginx -y



## Expected Resource Usage Profiles

### CPU-intensive workload
- High CPU utilisation across all available cores
- Increased context switching and scheduler activity
- Possible thermal throttling under sustained load conditions

### Memory-intensive workload
- Rapid allocation and deallocation of memory pages
- Increased swap usage if physical RAM limits are exceeded
- Useful for evaluating memory management and paging efficiency

### Disk I/O-intensive workload
- High volume of read and write operations
- Increased I/O wait times during peak activity
- Helps identify disk throughput limits and storage bottlenecks

### Network-intensive workload
- High packet transmission rates and bandwidth usage
- Observable latency under heavy traffic conditions
- Useful for analysing network stack performance and throughput limits

### Server application workload
- Moderate CPU and memory consumption under normal load
- Multiple worker processes handling concurrent connections
- Simulates realistic production-style server behaviour



### CPU-intensive workload
- High CPU utilisation across available cores
- Increased process scheduling activity
- Potential thermal throttling under sustained load

### Memory-intensive workload
- Rapid memory allocation
- Increased swap usage if RAM limits are exceeded
- Useful for evaluating memory management efficiency

### Disk I/O-intensive workload
- High read/write operations
- Increased I/O wait times
- Useful for identifying storage bottlenecks

### Network-intensive workload
- High throughput and packet transmission rates
- Observable latency under load
- Useful for analysing network limits

### Server application workload
- Moderate CPU and memory usage
- Multiple worker processes
- Realistic simulation of production server behaviour


## Monitoring Strategy

The following command-line tools will be used in later weeks to monitor system performance:

- `top` / `htop` – CPU and memory utilisation
- `free -h` – Memory usage statistics
- `vmstat` – System activity and swapping
- `iostat` – Disk I/O performance
- `ss` and `ip` – Network connections and statistics
- `systemctl status` – Service health monitoring

These tools provide quantitative metrics that support detailed analysis and performance optimisation.


## Weekly Reflection

This week improved my understanding of how different applications stress different operating system resources. Selecting appropriate workloads ensures that performance testing is meaningful rather than generic. Planning expected behaviour in advance also supports accurate interpretation of performance data and informed optimisation decisions in later stages of the coursework.
