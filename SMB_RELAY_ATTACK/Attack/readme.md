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

Check the **Connective** with **Ping**.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/06b7e11d6930849fa5650657ad1adafa2ed3b2ff/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20201402.png)

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

---

## Step 6: SMB Account Enumeration and Security Software Discovery

Information exposed through authenticated **SMB access** on the Windows target and identify **endpoint security**.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/06b7e11d6930849fa5650657ad1adafa2ed3b2ff/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20202408.png)

**Key Finding**

- Authenticated **SMB enumeration** exposed account and **security-principal** information from the target.
- **Windows 10 Pro**, build **19045 x64**.
- Name: **DESKTOP-F0P06SK**.
- The **RID enumeration** output included several account and security-principal names, including **Administrator, Guest,** DefaultAccount, WDAGUtilityAccount, Admin, and **user1**.

---

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/06b7e11d6930849fa5650657ad1adafa2ed3b2ff/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20202526.png)

**Key Finding**

**Sophos Intercept X (Endpoint Security)** — installed and running.

**Windows Defender** — installed.

---

## Step 7: Accessing the Windows Administrative Share Using SMBClient

Establish an **SMB session** with the **Windows target** to investigate **administrative share access**.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/f7ae4ab820ef462f79d64f0325293bb5e72bfa04/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20150744.png)

- The SMB client reached an interactive session.

- The prompt indicates that the connection was established.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/06b7e11d6930849fa5650657ad1adafa2ed3b2ff/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20201340.png)

---

































