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





![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/95bd2b14cc8bc63a64c87afba5ff09f694f269c2/SMB_RELAY_ATTACK/Find%26Protect/images/Screenshot%202026-10-21%20180953.png)
![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%203.png)
![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%204.png)
![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%205.png)
![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%206.png)
![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%207.png)
![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%208.png)
![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%209.png)
![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%209.5.png)
![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%2010.png)
![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%2011.png)
![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%2012.png)
![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%2013.png)
![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/d571357dcd035702025b965c2f64d9262794fe89/SMB_RELAY_ATTACK/Find%26Protect/images/img%2014.png)
