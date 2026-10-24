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



























## 🛡️ Recommended Mitigations

- Restrict SMB share access using least-privilege permissions.

- Avoid storing passwords in plaintext.

- Use a password manager or an approved secrets-management solution.

- Rotate any real credentials that may have been exposed.

- Audit SMB access and file-transfer activity.
