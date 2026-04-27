# Activity: Conduct a Security Audit (Botium Toys)

## 📋 Project Overview
This activity focused on performing a comprehensive security audit for **Botium Toys**. The goal was to evaluate the company's current security posture, identify gaps in their controls and compliance, and provide recommendations to align with industry standards like NIST CSF, PCI DSS, and SOC2.

---

## 🔍 Audit Objectives
1.  **Assess Security Controls:** Evaluate existing technical, operational, and physical controls.
2.  **Compliance Check:** Determine adherence to PCI DSS (for credit card data) and GDPR (for E.U. customer data).
3.  **Risk Mitigation:** Identify vulnerabilities and suggest immediate improvements to protect organizational assets.

---

## 🛠️ Controls & Compliance Checklist

### 1. Security Controls Assessment
| Control Type | Status | Best Practice Observed |
| :--- | :---: | :--- |
| **Firewall** | ✅ | Implemented to manage network traffic. |
| **Antivirus Software** | ✅ | Installed on systems to detect malware. |
| **Physical Locks** | ✅ | Used for offices, storefronts, and warehouses. |
| **CCTV Surveillance** | ✅ | Implemented for physical monitoring. |
| **Fire Detection** | ✅ | Fire alarms and sprinkler systems are in place. |
| **Least Privilege** | ❌ | Not currently enforced; needs implementation. |
| **Backups** | ❌ | No formal backup system identified. |
| **Encryption** | ❌ | Critical data is not encrypted in transit/rest. |
| **Password Policies** | ❌ | Weak or inconsistent password management. |

### 2. Compliance Checklist
* **PCI DSS:** Currently **Partial**. Adherence to secure credit card processing is required but encryption is missing.
* **GDPR:** Currently **Partial**. Privacy policies exist, but data classification and breach notification plans (72-hour rule) are not formalized.
* **SOC (Type 1 & 2):** **Incomplete**. User access policies and data integrity validation are missing.

---

## 📝 Findings & Recommendations

### Key Vulnerabilities
* **Access Control:** The lack of "Least Privilege" and "Separation of Duties" creates significant internal risks.
* **Data Protection:** Sensitive customer data (PII/SPII) is not encrypted, risking exposure during a breach.
* **Disaster Recovery:** The absence of a formal backup and recovery plan leaves the business vulnerable to ransomware or system failure.

### Recommendations for IT Manager
1.  **Implement IAM:** Enforce the principle of **Least Privilege** and implement a **Password Management System**.
2.  **Formalize Backups:** Establish a secure, offsite backup schedule for all critical business data.
3.  **Enhance Encryption:** Use AES-256 for data at rest and TLS for data in transit to meet **PCI DSS** standards.
4.  **Governance:** Develop a **Disaster Recovery Plan** and a **Breach Notification Protocol** to comply with GDPR.

---

## 🏁 Conclusion
By addressing these gaps, Botium Toys can significantly improve its security posture and ensure compliance with global data protection regulations. This audit serves as a roadmap for transitioning from an "at-risk" state to a robust, compliant environment.
