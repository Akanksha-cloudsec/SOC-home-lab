# 🛡️ DEFENSE

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/b1fc73416ef3aca4ee4621aa3e353316439c0d34/RDP_ATTACK/Find%26Protect/Images/img%201.png)

**Isolate the System**

---

## 🚨Step 1: Failed Login Alert in Microsoft Defender

Detect and investigate failed authentication attempts against the Windows 10 lab machine using Microsoft Defender's alert interface and Windows Security auditing logs.

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/135b057fc0ea5d6317bb7255c83618216a371812/RDP_ATTACK/Find%26Protect/Images/img%202.png)

**Key Findings**

- **Timestamp: October 20, 2026, 10:35:56 PM**
- **Severity: Medium**
- **Target Computer: DESKTOP-F0P06SK**
- **IP Address: 192.168.1.30**

**Sophos Central Detection: Failed Logon Attempts**

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/135b057fc0ea5d6317bb7255c83618216a371812/RDP_ATTACK/Find%26Protect/Images/img%202.1.png)

![image alt]()

**Key Finding**

- **Case severity: High**
- **Reported source IP: 192.168.1.30**

---

🛡️ **Step 2: RDP Attack Detection Using Microsoft Sentinel**

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/135b057fc0ea5d6317bb7255c83618216a371812/RDP_ATTACK/Find%26Protect/Images/img%202.3.png)

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/b1fc73416ef3aca4ee4621aa3e353316439c0d34/RDP_ATTACK/Find%26Protect/Images/img%204.png)

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/ded53db1992f572c35d9fadbf5ebdcfb22500352/RDP_ATTACK/Find%26Protect/Images/img%207.png)

**Key Finding**

- **Account Name: Admin**

| Event ID | Logon Type | Observed meaning | Time |
| --- | --- | --- | --- |
| 4625 | 3 | Failed network logon | 10:31:58 |
| 4624 | 3 | Successful network logon | 10:33:20 |
| 4624 | 10 | Successful remote interactive logon, commonly associated with RDP | 10:53:28 |

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/b1fc73416ef3aca4ee4621aa3e353316439c0d34/RDP_ATTACK/Find%26Protect/Images/img%202.2.png)


![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/b1fc73416ef3aca4ee4621aa3e353316439c0d34/RDP_ATTACK/Find%26Protect/Images/img%205.png)

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/ded53db1992f572c35d9fadbf5ebdcfb22500352/RDP_ATTACK/Find%26Protect/Images/img%206.png)

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/ded53db1992f572c35d9fadbf5ebdcfb22500352/RDP_ATTACK/Find%26Protect/Images/img%208.png)

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/ded53db1992f572c35d9fadbf5ebdcfb22500352/RDP_ATTACK/Find%26Protect/Images/img%209.png)

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/ded53db1992f572c35d9fadbf5ebdcfb22500352/RDP_ATTACK/Find%26Protect/Images/img%2010.png)

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/ded53db1992f572c35d9fadbf5ebdcfb22500352/RDP_ATTACK/Find%26Protect/Images/img%2011.png)

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/ded53db1992f572c35d9fadbf5ebdcfb22500352/RDP_ATTACK/Find%26Protect/Images/img%2012.png)

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/ded53db1992f572c35d9fadbf5ebdcfb22500352/RDP_ATTACK/Find%26Protect/Images/img%2013.png)

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/ded53db1992f572c35d9fadbf5ebdcfb22500352/RDP_ATTACK/Find%26Protect/Images/img%2014.png)

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/78311e05b1b3d41b9e1563da3b631a8decf94d69/RDP_ATTACK/Find%26Protect/Images/img%2015.5.png)

![image alt](https://github.com/Akanksha-cloudsec/SOC-home-lab/blob/78311e05b1b3d41b9e1563da3b631a8decf94d69/RDP_ATTACK/Find%26Protect/Images/img%2016.png)


























