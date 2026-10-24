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

## 🛰️ Step 3: Service Enumeration on the Windows Target

Identify **exposed network services** and their reported versions on the **discovered Windows host** to understand its **attack surface**.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/3056b510bf4c0d15ff617a4c93c6420c0446355b/RDP_ATTACK/Attack/Images/img%203.png)

**Key Findings**

- Port 445 (SMB): Open and relevant for investigating Windows file-sharing and authentication activity.
- Port 3389 (RDP): Open and relevant for investigating remote desktop logons.
- Ports 135 and 139: Indicate additional Windows RPC and NetBIOS services.

---

Started the Metasploit Framework from the Kali Linux terminal.

Selected the auxiliary RDP scanning module to check the target for an exposed RDP service.

Set the target IP address.

Ran the scanner against the target:

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/3056b510bf4c0d15ff617a4c93c6420c0446355b/RDP_ATTACK/Attack/Images/img%204.png)

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/3056b510bf4c0d15ff617a4c93c6420c0446355b/RDP_ATTACK/Attack/Images/img%205.png)

- **RDP** was detected on **192.168.1.31:3389**.
- The operating system was identified as **Windows 10.0.19041**.
- The scan completed against one host.

---

## 🔐 Step 4. RDP Authentication Testing Using Medusa

**Medusa** is a network login auditing tool available in **Kali Linux** that tests whether **usernames** and **passwords** can authenticate to **remote services**.

It can be used for **brute-force attacks**.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/3056b510bf4c0d15ff617a4c93c6420c0446355b/RDP_ATTACK/Attack/Images/img%206.png)

**Key Findings**

**User: Admin**           

**Password: Hacker26**

---

## Step 5. Successful RDP Connection from Kali Linux

Validate whether the credential identified during the previous authentication test could establish an interactive Remote Desktop session with the Windows target.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/3056b510bf4c0d15ff617a4c93c6420c0446355b/RDP_ATTACK/Attack/Images/img%207.png)

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/3056b510bf4c0d15ff617a4c93c6420c0446355b/RDP_ATTACK/Attack/Images/img%208.png)

**Key Finding**

- FreeRDP initiated a connection to 192.168.1.31.
- The Windows desktop was displayed in the remote session.
- The session used the Admin account.
- The Windows Command Prompt was opened within the remote desktop.
- The ipconfig command was executed to inspect network configuration.

---

## Step 6. Post-RDP Access: File Inspection and Credential Exposure

Document the activity performed after establishing an interactive RDP session with the Windows target and assess the exposure of sensitive information stored in local files.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/3056b510bf4c0d15ff617a4c93c6420c0446355b/RDP_ATTACK/Attack/Images/img%209.png)

**Activities Observed**

- Established an interactive RDP session with the Windows machine.
- Opened File Explorer and navigated to the Important file directory.
- Identified several files, including Adobe.exe, AdobeNew.exe, credential.txt, financial.txt, and paint.exe.
- Opened credential.txt in Notepad.
- Observed entries containing usernames and passwords stored in plaintext.

---

## Step 7. Ransomware Simulation After RDP Access

Impact of a simulated ransomware-like program executed on the Windows target after obtaining interactive RDP access.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/3056b510bf4c0d15ff617a4c93c6420c0446355b/RDP_ATTACK/Attack/Images/img%2010.png)

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/3056b510bf4c0d15ff617a4c93c6420c0446355b/RDP_ATTACK/Attack/Images/img%2011.png)

**Activities Observed**

- Navigated to the target user's desktop and file directories.
- Executed Adobe.exe from the Important file directory.
- Observed console output reporting that multiple files were being encrypted.
- Observed filenames with the .enc extension, including credential.txt.enc, financial.txt.enc, and other desktop files.
- Opened credential.txt.enc in Notepad. The displayed contents appeared unreadable, consistent with encrypted or otherwise transformed data.

---

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/ff8f190f47cb721025b140a676fda2712dfc3f3d/RDP_ATTACK/Attack/Images/img%2012.png)

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/ff8f190f47cb721025b140a676fda2712dfc3f3d/RDP_ATTACK/Attack/Images/img%2013.png)


















