# ⚔️ ATTACK

## 🌐 Step 1: Attacker Machine Network Configuration

Identify the **IP address** before conducting security testing against the Windows target machine in an isolated VirtualBox.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/3056b510bf4c0d15ff617a4c93c6420c0446355b/RDP_ATTACK/Attack/Images/img%201.png)

**Attacker machine: Kali Linux**  
**IP address: 192.168.1.30**

---

## 🔎 Step 2: Network Discovery Using Nmap

Identify **active hosts** on the local lab network to determine which machines may be relevant to the subsequent security assessment.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/3056b510bf4c0d15ff617a4c93c6420c0446355b/RDP_ATTACK/Attack/Images/img%202.png)

The scan identified **192.168.1.31** as a **host** with a MAC address associated with an Oracle VirtualBox virtual network interface. This makes it a candidate for further identification within the lab.

---
