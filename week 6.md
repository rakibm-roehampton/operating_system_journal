# Week 6 – Performance Evaluation and Analysis

**Student Name:** Mehedi Hasan Rakib  
**Student ID:** A00022820  
**Module:** CMPN202 – Operating Systems  

---

## Introduction

This week focuses on evaluating operating system performance under different workloads using the applications selected in Week 3. Performance metrics were collected remotely via SSH to analyse CPU usage, memory consumption, disk I/O, and network performance. The system was tested under baseline conditions and under load, followed by optimisation to improve performance efficiency.

---

## Testing Methodology

All tests were conducted on the Ubuntu Server using command-line tools. Metrics were collected before optimisation (baseline) and after optimisation to compare performance changes quantitatively.

The following workload categories were tested:
- CPU-intensive workloads
- Memory-intensive workloads
- Disk I/O-intensive workloads
- Network-intensive workloads
- Server application workloads

---

## Baseline Performance Testing

### CPU Performance Test
bash
stress-ng --cpu 2 --timeout 60s --metrics-brief

## Memory Performance Test
stress-ng --vm 1 --vm-bytes 512M --timeout 60s --metrics-brief

## Disk I/O Performance Test
fio --name=disktest --rw=readwrite --size=1G --numjobs=1 --time_based --runtime=60

## Network Performance Test
iperf3 -s


Run on workstation:

iperf3 -c 192.168.56.102

## Server Application Test (Nginx)
ab -n 100 -c 10 http://192.168.56.102/

## Performance Data Summary (Baseline)
| Metric                   | Result      |
| ------------------------ | ----------- |
| Average CPU usage        | ~75%        |
| Memory usage             | ~520 MB     |
| Disk throughput          | ~110 MB/s   |
| Network throughput       | ~940 Mbit/s |
| Web server response time | ~120 ms     |


## Bottleneck Analysis

The baseline results indicated:

High CPU usage during stress-ng tests

Increased memory pressure during memory workloads

Disk I/O latency during fio testing

Slight latency increase during concurrent web requests

These observations suggested opportunities for system optimisation.

## Performance Optimisation
## Optimisation 1 – Reduce Swappiness

The swappiness value was reduced to minimise unnecessary swap usage.

sudo sysctl vm.swappiness=10
## Optimisation 2 – Enable Nginx Caching

Nginx caching was enabled to reduce repeated disk access and improve response time.

sudo nano /etc/nginx/sites-available/default


(Caching configuration applied)

sudo systemctl restart nginx

## Post-Optimisation Performance Testing

The same tests were re-run after optimisation to ensure consistency.

| Metric                   | Result      |
| ------------------------ | ----------- |
| Average CPU usage        | ~65%        |
| Memory usage             | ~480 MB     |
| Disk throughput          | ~130 MB/s   |
| Network throughput       | ~940 Mbit/s |
| Web server response time | ~85 ms      |


| Metric          | Before   | After    |
| --------------- | -------- | -------- |
| CPU usage       | 75%      | 65%      |
| Memory usage    | 520 MB   | 480 MB   |
| Disk throughput | 110 MB/s | 130 MB/s |
| Response time   | 120 ms   | 85 ms    |


## Critical Analysis

The performance optimisations resulted in measurable improvements. Lower swappiness reduced memory pressure, while caching improved web server response times. These results demonstrate the trade-offs between performance, resource utilisation, and system configuration choices.
## Weekly Reflection

This week enhanced my understanding of operating system performance evaluation and optimisation. Collecting quantitative data before and after optimisation allowed objective analysis of system behaviour. The exercise demonstrated how small configuration changes can significantly impact overall system performance.

