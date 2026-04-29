# Incident Report Analysis – NIST Cybersecurity Framework (CSF)

## Incident Summary

| Function | Analysis |
|---|---|
| Summary | The organization experienced a Denial-of-Service (DoS) attack that disrupted internal network operations for approximately two hours. Thousands of malicious ICMP packets overwhelmed the servers, preventing access to internal resources. Investigation revealed that the attacker exploited an improperly configured firewall. The security team contained the attack by blocking malicious traffic and implementing stronger security controls, including firewall rate limiting, source IP verification, network monitoring, and IDS/IPS filtering. |
| Identify | The security team reviewed systems, network devices, and access policies to identify vulnerabilities. They confirmed that excessive ICMP traffic targeted internal servers and exploited firewall misconfigurations, resulting in service disruption and resource exhaustion. |
| Protect | To improve protection, firewall policies were reconfigured, stricter traffic filtering rules were applied, and IDS/IPS solutions were strengthened. Additional network monitoring tools were introduced to reduce exposure to future DoS attacks. |
| Detect | Continuous traffic monitoring was enhanced using network monitoring software to detect unusual ICMP traffic patterns and improve early threat detection capabilities. |
| Respond | The security team blocked malicious ICMP traffic, reconfigured firewall rules, and implemented IDS/IPS filtering to contain the attack and prevent further disruption. |
| Recover | Critical services were restored, firewall security gaps were corrected, and monitoring was continued to ensure normal network operation. Response plans were reviewed to reduce the likelihood of similar incidents in the future. |

---

## Reflections / Lessons Learned

This incident demonstrated that security controls alone are not enough unless they are properly configured, maintained, and continuously monitored. Even when defensive systems cannot fully prevent an attack, proper configuration significantly reduces the attack surface and limits operational damage.
