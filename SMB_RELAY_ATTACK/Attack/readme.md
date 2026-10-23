# ⚔️ ATTACK

## 🌐 Step 1: Attacker Machine Network Configuration

Identify the **IP address** before conducting security testing against the Windows target machine in an isolated VirtualBox.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/9520872342d935c2cfe8a2b0f0f93842afd60c9b/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20150239.png)

**Attacker machine: Kali Linux**  
**IP address: 192.168.1.24**

---

## 🔎 Step 2: Network Discovery Using Nmap

Identify **active hosts** on the local lab network to determine which machines may be relevant to the subsequent security assessment.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/27cbb623b0a7bde0c68c05e1895b9617996e5483/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20150325.png)

The scan identified **192.168.1.16** as a **host** with a MAC address associated with an Oracle VirtualBox virtual network interface. This makes it a candidate for further identification within the lab

Check the **Connective** with **Ping**.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/06b7e11d6930849fa5650657ad1adafa2ed3b2ff/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20201402.png)

---

## 🛰️ Step 3: Service Enumeration on the Windows Target

Identify **exposed network services** and their reported versions on the **discovered Windows host** to understand its **attack surface**.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/27cbb623b0a7bde0c68c05e1895b9617996e5483/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20150428.png)

**Key Findings**

- Port 445 (SMB): Open and relevant for investigating Windows file-sharing and authentication activity.

- Port 3389 (RDP): Open and relevant for investigating remote desktop logons.

- Ports 135 and 139: Indicate additional Windows RPC and NetBIOS services.

---

## 🔐 Step 4: SMB Authentication Testing Using CrackMapExec

**CrackMapExec** is a **network security testing tool** commonly used to assess Windows networks, especially **SMB** and **Active Directory** environments.

It can be used for **brute-force attacks**.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/27cbb623b0a7bde0c68c05e1895b9617996e5483/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20150551.png)

**Key Findings**

**User: Admin**           

**Password: Hacker26**

---

## 📂 Step 5: SMB Share Enumeration Using SMBMap

**Enumerate SMB shares** on the **Windows target** and assess the **permissions** available to the **authenticated** lab account.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/f7ae4ab820ef462f79d64f0325293bb5e72bfa04/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20150647.png)

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/f7ae4ab820ef462f79d64f0325293bb5e72bfa04/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20150705.png)

- **Authentication succeeded**: **SMBMap** displayed Status: **ADMIN!!!**.

- **Administrative shares were accessible**: **ADMIN$** and **C$** were listed with **read/write** permissions.

- **Potential security impact**: If these permissions are available to an **unauthorized** or **compromised account**, they may **permit access to sensitive files** or **enable unauthorized file** modifications.

---

## 🖥️ Step 6: SMB Account Enumeration and Security Software Discovery

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

## 🖥️ Step 7: Accessing the Windows Administrative Share Using SMBClient

Establish an **SMB session** with the **Windows target** to investigate **administrative share access**.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/f7ae4ab820ef462f79d64f0325293bb5e72bfa04/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20150744.png)

- The SMB client reached an interactive session.

- The prompt indicates that the connection was established.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/06b7e11d6930849fa5650657ad1adafa2ed3b2ff/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20201340.png)

---

## 📁 Step 8: Windows File-System Enumeration via SMB

Investigate which directories are visible through an authenticated SMB session to the Windows target. 

Connect to the **C$ Share**. After entering the password, the **SMB client** opened an **interactive session**. 

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/fdab75c73ab7e09f9b7cbd2ed4e30a1ff728a056/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20201442.png)

Enumerate **User** Profiles.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/fdab75c73ab7e09f9b7cbd2ed4e30a1ff728a056/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20201540.png)

- The output showed profile directories named **Admin** and **user1**.

---

## 📂 Step 9: Enumerating the Admin User's SMB Share and Identifying Sensitive Files

Enumerate the contents of the **Admin's directory** on an **SMB share**and identify potentially sensitive files for security investigation.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/682afa7b6496a79351b412490976bc2b616e177e/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20201631.png)

The directory listing reveals several user-profile folders, including Documents, Downloads, Desktop, and Cookies. It also shows a directory named **Important file**.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/682afa7b6496a79351b412490976bc2b616e177e/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20201751.png)

**Key Finding**

- **credential.txt**

- **financial.txt**

---

## 📄 Step 10: Downloading Sensitive Files from an SMB Share

Demonstrate how files identified during **SMB share enumeration** can be downloaded to a local machine when the current **SMB session** has sufficient permissions.

Set the local download directory.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/682afa7b6496a79351b412490976bc2b616e177e/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20201834.png)

The SMB client downloads **credential.txt** and **financial.txt** from the remote directory to the specified local directory.

---

## 📄 Step 11: Uploading Executable Files to an SMB Share

Document how files from a local machine can be transferred to a remote SMB share when the established session has sufficient write permissions.

Set the local working directory.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/682afa7b6496a79351b412490976bc2b616e177e/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20201948.png)

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/682afa7b6496a79351b412490976bc2b616e177e/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20202054.png)

The SMB client transfers **encryption.exe** and **launcher.exe** from the local machine to the remote SMB directory.

---

## 📄 Step 12: Renaming Executables on an SMB Share

Document file renaming and additional file uploads through an established SMB session, demonstrating the ability to modify files within the remote directory.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/682afa7b6496a79351b412490976bc2b616e177e/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20202229.png)

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/682afa7b6496a79351b412490976bc2b616e177e/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20202135.png)

This command attempts to change the remote filename from launcher.exe to paint.exe.

**Remote file modification:** The SMB session allows file operations within the remote directory.

**Misleading filenames:** Names such as Adobe.exe or paint.exe can make an executable appear legitimate, potentially complicating detection.

---

## 📄 Step 13: Inspecting Downloaded Files and Identifying Exposed Credentials

Verify the contents of files retrieved from the SMB share and assess the potential impact of sensitive information exposure.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/faeca5c411b8784b73bc1c3d2dc00fed664a058b/SMB_RELAY_ATTACK/Attack/images/Screenshot%202026-10-20%20203656.png)

**Key Finding**

- **Credential exposure:** The downloaded file contains apparent usernames and plaintext passwords.

- **Financial information:** The second file contains company-related text, although the screenshot does not establish that it contains actual financial records.

- **Data confidentiality:** The ability to retrieve and read these files demonstrates that information accessible through the SMB share could be exposed to a user with the current session's permissions.







