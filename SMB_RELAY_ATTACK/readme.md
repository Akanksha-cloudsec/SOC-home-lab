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

## 🔐 4. Technical Analysis

### 4.1 Failed authentication followed by successful authentication

Event ID 4625 records a failed logon. Event ID 4624 records a successful logon. Their proximity in time makes it appropriate to investigate whether the successful logon followed the failed attempt.

The successful event has these reported attributes:

- Account: Admin
- Source IP: 192.168.1.24
- Workstation: KALI
- Authentication package: NTLM
- Logon type: 3 — network logon

Interpretation: This is consistent with authentication over a network, including SMB. Logon Type 3 is not itself proof of a brute-force attack, SMB relay, or pass-the-hash activity.

### 4.2 Administrative share access

Event ID 5140 recorded access to ADMIN$ and C$.

- ADMIN$ is a Windows administrative share associated with the Windows directory.
- C$ is an administrative share for the C: drive.
- The reported access mask 0x1 represents a read-data or list-directory access right, depending on the object type.

**Interpretation:** The events support network access to administrative shares. They do not alone prove that a file was downloaded, copied, or changed.

### 4.3 Detailed file-share access

Event ID 5145 provides details about access checks against shared files and directories.

The reported paths included:

- Users
- Users\Admin\Important file
- credential.txt
- financial.txt
- encryption.exe
- Launcher.exe
- decryption.exe

These events establish that Windows evaluated requested access to the specified share objects. To determine the exact activity, the full event fields—including the share name, relative target name, access mask, object type where available, and outcome—must be examined.

### 4.4 Access-mask interpretation

| Access mask | Interpretation | Limitation |
|---|---|---|
| `0x1` | Read data for a file or list directory contents for a directory | Does not prove a complete file download |
| `0x81` | `0x80` plus `0x1`: read attributes and read data/list directory | Does not prove a modification |
| `0x2` | Write data for a file or add a file to a directory | A requested access right is not, by itself, proof that a write succeeded |
| `0x10000` | `DELETE` access right | Does not prove deletion or renaming actually occurred |
| `0x120089` | Combination of requested rights, including `DELETE` | Requires full event context to determine what was attempted and whether it succeeded |
| `0x12019f` | Combination of requested access rights, including `DELETE` and additional file or standard rights | Does not by itself prove execution, encryption, or a successful file change |

A rename operation can involve delete rights on the original object and appropriate rights on the destination or parent directory. A 0x10000 event alone is not enough to confirm a rename.












## 🛡️ Recommended Mitigations

- Restrict SMB share access using least-privilege permissions.

- Avoid storing passwords in plaintext.

- Use a password manager or an approved secrets-management solution.

- Rotate any real credentials that may have been exposed.

- Audit SMB access and file-transfer activity.
