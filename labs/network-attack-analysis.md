# Incident Report: Network Attack Analysis (SYN Flood)

## Section 1: Attack Identification
**Case Overview:**
The organization's web server recently experienced a significant connection timeout error, rendering the website inaccessible to users. 

**Investigation Findings:**
* **Initial Assessment:** The web server was likely experiencing a **Denial of Service (DoS)** attack.
* **Log Evidence:** Forensic log analysis revealed an abnormal volume of **TCP SYN** packets originating from an unfamiliar IP address (**203.0.113.0**) targeting the company’s web server (**192.0.2.1**).
* **Conclusion:** This event is classified as a **SYN Flood attack**.

---

## Section 2: Technical Breakdown of the Attack

### TCP Handshake Protocol Overview
Under normal conditions, a legitimate connection follows the **three-way handshake** process:
1.  **SYN:** Client sends a synchronization packet.
2.  **SYN/ACK:** Server acknowledges and reserves system resources.
3.  **ACK:** Client sends an acknowledgment to finalize the connection.

### Analysis of the Malfunction
The investigation reveals that a malicious actor exploited this mechanism by flooding the server with a massive volume of **SYN** packets from IP **203.0.113.0**. 

The attacker intentionally withheld the final **ACK** packets, forcing thousands of connections to remain in a **"half-open"** state. This led to the exhaustion of the server’s memory and CPU resources as it remained in a perpetual waiting state for responses that never arrived.

---

## Section 3: System Impact and Service Disruption

### Resource Exhaustion
The rapid influx of SYN requests effectively overwhelmed the server's capacity, causing the system to become completely unresponsive to legitimate internal requests.

### Critical Failures Observed:
* **Service Unavailability:** Users encountered **504 Gateway Time-out** errors, indicating the server could not complete requests in time.
* **Connection Resets:** Network logs showed a high frequency of **[RST, ACK]** flags, signifying forced connection terminations.
* **Business Impact:** Access to the **Sales Page** was effectively blocked, resulting in a total disruption of business operations during the attack window.

---

## Key Skills Demonstrated
* **Network Forensics:** Identifying attack patterns through log analysis.
* **TCP/IP Protocol Analysis:** Deep understanding of the three-way handshake and its vulnerabilities.
* **Incident Classification:** Distinguishing between regular traffic spikes and malicious DoS attacks.
* **Impact Assessment:** Evaluating business and technical disruptions caused by security breaches.
