# 🛡️ SOC-home-lab SIEM & EDR Security Monitoring
# [Sentinel(SIEM), Sophos(EDR), VM Kali Linux(Attacker), VM win 10, 11, Ubuntu(Victims)]

A hands-on Security Operations Center (SOC) Home Lab built to simulate real-world cyber attacks, security monitoring, threat detection, investigation, and incident response in a controlled virtual environment.

The lab integrates Microsoft Sentinel (SIEM) and Sophos (EDR) with multiple virtual machines to simulate an attacker and different victim environments.

---

## 📋 Table of Contents
- <a href="#architecture-diagram">Architecture Diagram</a>
- <a href="#key-features">Key Features</a>
- [SMB_Relay_Attack](https://github.com/Akanksha-cloudsec/SOC-home-lab/tree/d07b011a62640e8d0c8698c6e8fec4b0821d9315/SMB_RELAY_ATTACK)

  - [Attack](https://github.com/Akanksha-cloudsec/SOC-home-lab/tree/79138e0bc9948dc0e56081d73fa4889ef036d5da/SMB_RELAY_ATTACK/Attack)
  - [Defense](https://github.com/Akanksha-cloudsec/SOC-home-lab/tree/79138e0bc9948dc0e56081d73fa4889ef036d5da/SMB_RELAY_ATTACK/Find%26Protect)
 
- [RDP_&_Ransomware_Attack](https://github.com/Akanksha-cloudsec/SOC-home-lab/tree/a5a4e275d65eb0f7ad29d68db84009c82433175a/RDP_ATTACK)

  - [Attack](https://github.com/Akanksha-cloudsec/SOC-home-lab/tree/a5a4e275d65eb0f7ad29d68db84009c82433175a/RDP_ATTACK/Attack)
  - [Defense](https://github.com/Akanksha-cloudsec/SOC-home-lab/tree/a5a4e275d65eb0f7ad29d68db84009c82433175a/RDP_ATTACK/Attack)

<h2><a class="anchor" id="architecture-diagram"></a> 🏗️ Architecture Diagram</h2>

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/a33e90b2b25f48679955ee7e2c4d6f37f784dd6e/Architecture%20Diagram/Architecture_Diagram.png)

---

<h2><a class="anchor" id="key-features"></a> 🎯 Key Features</h2>

**The lab is used to practice the complete SOC workflow:**

1. **Reconnaissance & Attack Simulation**

 - Network discovery
 - Port and service enumeration
 - Controlled attack scenarios from Kali Linux
2. **Security Monitoring**
 - Windows and Linux log collection
 - Endpoint activity monitoring
 - Authentication and process monitoring
 - File activity investigation
 - Network activity analysis
3. **Threat Detection**
 - Microsoft Sentinel KQL queries
 - Scheduled and Near Real-Time (NRT) analytics rules
 - Suspicious login detection
 - After-hours activity detection
 - Process and file activity detection
 - Correlation of security events
4. **Endpoint Detection & Response**
 - Sophos EDR alerts
 - Endpoint investigation
 - Suspicious activity analysis
 - Threat containment and response
5. **Incident Investigation**
 - Alert → Incident → Investigation
 - Identifying affected users and machines
 - Investigating attacker activity
 - Analyzing timestamps, IP addresses, processes, and files
 - Developing Indicators of Compromise (IOCs)
