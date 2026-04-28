# Threat Modeling Analysis: PASTA Framework (Sneaker Company)

## Overview
This report documents the application of the **PASTA (Process for Attack Simulation and Threat Analysis)** methodology for a sneaker e-commerce platform. The goal was to align business objectives with technical security requirements to protect user data and ensure platform integrity.

---

## Stage I: Define Business and Security Objectives
* **Operational Efficiency:** Ensure a seamless and high-quality user experience for both buyers and sellers within the platform.
* **Secure Communication:** Facilitate reliable and encrypted communication channels between buyers and sellers to prevent fraud and social engineering.
* **Data Privacy & Identity Management:** Implement robust account management systems to ensure the confidentiality, integrity, and availability (CIA) of user personal and financial data.

---

## Stage II: Define the Technical Scope
**Priority Assets:** SQL Database & API Endpoints.
Based on common threat actor behaviors, the SQL database is designated as the highest priority for security evaluation. Since the application handles sensitive customer data and payment information, the primary focus is on securing the backend from **SQL Injection (SQLi)** attacks. 

**Defense Strategy:** Implementing defense-in-depth strategies such as salting and hashing to ensure that even in the event of a data breach, the exfiltrated data remains cryptographically useless to unauthorized parties.

---

## Stage III: Decompose the Application
*(Analysis based on data flow diagrams to identify entry points and potential vulnerabilities within the sneaker platform architecture.)*

---

## Stage IV: Threat Analysis
### External Threats:
* **Phishing and Social Engineering:** Targeting administrative staff to gain unauthorized access to internal systems or sensitive credentials.
* **Automated Attacks:** Brute-force attacks against authentication interfaces and session hijacking to compromise user accounts.

### Internal Threats:
* **Accidental Data Loss:** Unintentional modification or deletion of the production database by authorized personnel due to human error.

---

## Stage V: Vulnerability Analysis
* **Improper Input Validation:** Vulnerable input fields in the authentication UI that do not properly sanitize user-supplied data, allowing the execution of malicious SQL queries.
* **Broken Authentication & Weak Session Management:** Absence of Multi-Factor Authentication (MFA) and lack of Rate Limiting mechanisms, leaving the application susceptible to credential stuffing and brute-force attempts.

---

## Stage VI: Attack Modeling
*(Analysis involves the creation of attack tree diagrams to visualize potential exploit paths for the identified threats.)*

---

## Stage VII: Risk Analysis and Impact
To mitigate the identified risks, the following security controls are recommended:

1.  **Parameterized Queries:** Enforce the use of prepared statements to mitigate SQL Injection risks at the code level.
2.  **Multi-Factor Authentication (MFA):** Implement mandatory MFA for all users, specifically for administrative and seller accounts, to provide an extra layer of identity assurance.
3.  **Account Lockout & Rate Limiting:** Deploy security controls to monitor and block repetitive failed login attempts from a single IP or account to thwart brute-force attacks.
4.  **Advanced Cryptographic Protections:** Utilize **SHA-256** with unique salts for password storage and **AES-256** for encrypting sensitive payment data at rest.
