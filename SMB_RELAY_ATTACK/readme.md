# 📝 SOC Incident Investigation Report — SMB Authentication and File-Share Activity 

## 📌 1. Incident Overview

This investigation was conducted in an isolated VirtualBox SOC lab using Kali Linux as the testing workstation and Windows 10 as the target system. Microsoft Sentinel was used to investigate Windows Security events and analyze SMB authentication and file-share activity.

| Field | Details |
|---|---|
| Investigation date | October 20, 2026 |
| Target computer | `DESKTOP-F0P06SK` |
| Severity | `Medium` |
| Source IP | `192.168.1.24` |
| Source workstation | `KALI` |
| Account | `Admin` |
| Authentication package | NTLM |
| Primary logon event | Windows Event ID `4624` |
| Primary share-access events | Windows Event IDs `5140`, `5145` |
| Environment | Authorized isolated SOC lab |
| Investigation status | Evidence review in progress |

## 📂 2. Executive Summary

On October 20, 2026, a Medium-severity failed-logon alert was recorded for the Windows target DESKTOP-F0P06SK, identifying 192.168.1.24 as the source IP address.

At approximately 3:51 PM, Windows Security logs recorded a successful network logon associated with the Admin account. The workstation name was KALI, and NTLM was used as the authentication package. Subsequent events documented access to the ADMIN$ and C$ administrative shares and detailed access checks involving files and directories under Users\Admin\Important file.

Later events included access checks involving encryption.exe, Launcher.exe, and decryption.exe. These filenames warrant further investigation, but their names and the access masks alone do not establish malicious execution or successful encryption.

## 🕒 3. Incident Timeline

The following timeline is based on the timestamps and event details collected during the investigation. Times are shown in IST (UTC+05:30).

| Timestamp (IST) | Event ID | Activity | Observation |
|---|---:|---|---|
| 3:50:56 PM | 4625 | Failed logon | Medium-severity alert associated with source IP `192.168.1.24` |
| 3:51:56 PM | 4624 | Successful logon | Account `Admin`; workstation `KALI`; NTLM authentication |
| 3:51:56 PM | 5140 | Network share access | `ADMIN$` share |
| 3:56:00 PM | 5140 | Network share access | `C$` administrative share |
| 3:56:28 PM | 5145 | Detailed share access check | `Users` directory |
| 3:58:35 PM | 5145 | Detailed share access check | `Users\Admin\Important file` |
| 4:04:10 PM | 5145 | File access check | `credential.txt` |
| 4:04:35 PM | 5145 | File access check | `financial.txt` |
| 4:06:59 PM | 5145 | File access checks | `encryption.exe` |
| 4:15:02 PM | 5145 | File access checks | `Launcher.exe` |
| 4:17:11 PM | 5145 | Additional access check | `encryption.exe` |
| 4:17:39 PM | 5145 | Additional access check | `Launcher.exe` |
| 4:19:31 PM | 5145 | File access checks | `decryption.exe` |
| 4:21:03 PM | 5145 | Additional access check | `decryption.exe` |
























## 🛡️ Recommended Mitigations

- Restrict SMB share access using least-privilege permissions.

- Avoid storing passwords in plaintext.

- Use a password manager or an approved secrets-management solution.

- Rotate any real credentials that may have been exposed.

- Audit SMB access and file-transfer activity.
