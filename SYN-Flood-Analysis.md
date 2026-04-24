# Lab Report: SYN Flood Attack Analysis

## 1. Attack Identification
During the investigation of a website connection timeout, the following was observed:
* **Symptom:** Web server experiencing a Denial of Service (DoS).
* **Evidence:** Analysis of logs showed a massive volume of **TCP SYN** packets from a single unfamiliar IP address (`203.0.113.0`).
* **Target:** The company's web server at `192.0.2.1`.
* **Conclusion:** This activity confirms a **SYN Flood attack**.

---

## 2. Technical Breakdown
### The TCP Three-Way Handshake
Under normal conditions, a connection is established as follows:
1. **SYN:** Client requests synchronization.
2. **SYN/ACK:** Server acknowledges and waits.
3. **ACK:** Client completes the connection.

### The Mechanism of Failure
In this attack, the malicious actor sent SYN requests but never sent the final **ACK**. This left thousands of connections in a **"half-open"** state, consuming all available server resources (CPU and Memory) until the server could no longer respond to legitimate users.

---

## 3. Impact & Service Disruption
* **Service Unavailability:** Legitimate users received **504 Gateway Time-out** errors.
* **System Logs:** High frequency of `[RST, ACK]` flags were recorded.
* **Business Impact:** The **Sales Page** became inaccessible, leading to a complete halt in online business operations.
