# 🛡️ DEFENSE

## 🚨Step 1: Failed Login Alert in Microsoft Defender

Detect and investigate failed authentication attempts against the Windows 10 lab machine using Microsoft Defender's alert interface and Windows Security auditing logs.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/9d787f0d19110bac9cbc85ee061d6214aa1f40fc/SMB_RELAY_ATTACK/Find%26Protect/images/img%201.png)

**Key Findings**

- **Timestamp: October 20, 2026, 3:50:56 PM**
- **Severity: Medium**
- **Target Computer: DESKTOP-F0P06SK**
- **IP Address: 192.168.1.24**
  
---

## 🔍 Step 2: Authentication Investigation in Microsoft Sentinel

Investigate Windows authentication events in Microsoft Sentinel to identify activity originating from the Kali Linux machine and correlate successful logons with previously detected failed login attempts.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/95bd2b14cc8bc63a64c87afba5ff09f694f269c2/SMB_RELAY_ATTACK/Find%26Protect/images/Screenshot%202026-10-21%20173902.png)

**Key Finding**

- **Account: Admin**
- **First seen: Oct 20, 2026, 3:51:56.525 PM**
- **EventID: 4624 (Successful Logins)**
- **TotalEvents: 8**

---

Investigate successful network logons originating from the Kali Linux machine and identify the account, authentication protocol, and logon type using Microsoft Sentinel.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/95bd2b14cc8bc63a64c87afba5ff09f694f269c2/SMB_RELAY_ATTACK/Find%26Protect/images/Screenshot%202026-10-21%20180953.png)

**Key Finding**

- **Event Time: Oct 20, 2026, 3:51:56.525 PM**
- **Workstation Name: KALI**
- **Authentication Package: NTLM**
- **Logon Type: 3 (Network)**

---

## 🔍 Step 3: Investigating Successful SMB Network Logons in Microsoft Sentinel

Investigate Windows network-share access events to determine which SMB shares were accessed during the controlled lab.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%203.png)

**Key Finding**

- **TimeStamp: Oct 20,2026, 3:51:56.537 PM**
- **EventID: 5140 (Network Shared network)**
- **SharedName:ADMIN**
- **AccessMask: 0x1 (Read a Shared file)**

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%204.png)

**Key Finding**

- **TimeStamp: Oct 20,2026, 3:53:14.835 PM**
- **EventID: 5140 (Network Shared network)**
- **SharedName: ADMIN**
- **RelativeTargetName: system32**
- **AccessMask: 0x80 (Read file attributes)**

---

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%205.png)

**Key Finding**

- **TimeStamp: Oct 20,2026, 3:56:00.186 PM**
- **EventID: 5140 (Network Shared network)**
- **SharedName: C (C drive)**
- **AccessMask: 0x1 (Read a Shared file)**

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%206.png)

**Key Finding**

- **TimeStamp: Oct 20,2026, 3:56:28.638 PM**
- **EventID: 5145 (Detailed File Share Check)**
- **SharedName: C (C drive)**
- **RelativeTargetName: Users**
- **AccessMask: 0x81 (READ_ATTRIBUTES (0x80) and READ_DATA (0x01))**

---

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%207.png)

**Key Finding**

- **TimeStamp: Oct 20,2026, 3:58:35.023 PM**
- **RelativeTargetName: Users\Admin\Important file**
- **AccessMask: 0x81 (READ_ATTRIBUTES (0x80) and READ_DATA (0x01))**

---

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%208.png)

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%209.png)

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%209.5.png)

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%2010.png)

**Key Finding**

| **RelativeTargetName** | **AccessMask** | **Time Shown** |
| :--- | :--- | :--- |
| encryption.exe | 0x12019f | 4:06:59 PM |
| financial.txt | 0x120089 | 4:04:35 PM |
| credential.txt | 0x120089 | 4:04:10 PM |
| encryption.exe | 0x2 | 4:06:59 PM |
| encryption.exe | 0x10000| 4:17:11 PM |

0x12019f : A combination of read, write, execute/traverse, attribute, delete-child, and security-related permissions.

0x120089 : A combination of read data/list directory, read attributes, read extended attributes, and read permissions.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%2010.png)
![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%2011.png)
![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%2012.png)
![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%2013.png)
![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%2014.png)
