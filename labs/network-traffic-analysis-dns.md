# Incident Report: Network Traffic & DNS Analysis

## Part 1: Investigation Summary (DNS & ICMP Traffic)
**Scenario:** Customers reported an inability to access the "Yummy Recipes" website, leading to a connection timeout investigation.

**Network Traffic Logs (UDP/ICMP):**
The following table represents the forensic data captured during the communication failure:

| No. | Time | Source | Destination | Protocol | Length | Info |
|-----|------|--------|-------------|----------|--------|------|
| 47 | 49.0131 | 10.128.209.22 | 172.67.187.21 | ICMP | 74 | Destination unreachable (Port 53 unreachable) |
| 48 | 49.0283 | 10.128.209.22 | 172.67.187.21 | ICMP | 74 | Destination unreachable (Port 53 unreachable) |
| 49 | 49.0311 | 10.128.209.22 | 172.67.187.21 | ICMP | 74 | Destination unreachable (Port 53 unreachable) |
| 50 | 49.4575 | 10.128.209.22 | 172.67.187.21 | ICMP | 74 | Destination unreachable (Port 53 unreachable) |
| 51 | 50.7366 | 10.128.209.22 | 172.67.187.21 | ICMP | 74 | Destination unreachable (Port 53 unreachable) |
| 52 | 52.6554 | 10.128.209.22 | 172.67.187.21 | ICMP | 74 | Destination unreachable (Port 53 unreachable) |

**Analysis of Findings:**
The recurring error message **"Destination unreachable (Port 53 unreachable)"** indicates a failure in DNS resolution. Since Port 53 is the standard port for DNS, the likely cause of the outage is either a server-side failure or an attack blocking DNS responses.
