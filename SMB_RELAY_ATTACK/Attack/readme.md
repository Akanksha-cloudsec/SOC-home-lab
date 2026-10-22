# Attack 

## **Step 1: Attacker Machine Network Configuration**

Identify the **IP address** before conducting security testing against the Windows target machine in an isolated VirtualBox.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/9520872342d935c2cfe8a2b0f0f93842afd60c9b/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20150239.png)

**Attacker machine: Kali Linux**  
**IP address: 192.168.1.24**

---

## Step 2: Network Discovery Using Nmap

Identify **active hosts** on the local lab network to determine which machines may be relevant to the subsequent security assessment.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/27cbb623b0a7bde0c68c05e1895b9617996e5483/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20150325.png)

The scan identified **192.168.1.16** as a **host** with a MAC address associated with an Oracle VirtualBox virtual network interface. This makes it a candidate for further identification within the lab

---

## Step 3: Service Enumeration on the Windows Target

Identify **exposed network services** and their reported versions on the **discovered Windows host** to understand its **attack surface**.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/27cbb623b0a7bde0c68c05e1895b9617996e5483/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20150428.png)

**Key Findings**

- Port 445 (SMB): Open and relevant for investigating Windows file-sharing and authentication activity.

- Port 3389 (RDP): Open and relevant for investigating remote desktop logons.

- Ports 135 and 139: Indicate additional Windows RPC and NetBIOS services.

---

## Step 4: SMB Authentication Testing Using CrackMapExec

**CrackMapExec** is a **network security testing tool** commonly used to assess Windows networks, especially **SMB** and **Active Directory** environments.

It can be used for **brute-force attacks**.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/27cbb623b0a7bde0c68c05e1895b9617996e5483/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20150551.png)

**Key Findings**

**User: Admin**           

**Password: Hacker26**

---

## Step 5: SMB Share Enumeration Using SMBMap

**Enumerate SMB shares** on the **Windows target** and assess the **permissions** available to the **authenticated** lab account.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/f7ae4ab820ef462f79d64f0325293bb5e72bfa04/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20150647.png)

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/f7ae4ab820ef462f79d64f0325293bb5e72bfa04/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20150705.png)

- **Authentication succeeded**: **SMBMap** displayed Status: **ADMIN!!!**.

- **Administrative shares were accessible**: **ADMIN$** and **C$** were listed with **read/write** permissions.

- **Potential security impact**: If these permissions are available to an **unauthorized** or **compromised account**, they may **permit access to sensitive files** or **enable unauthorized file** modifications.































