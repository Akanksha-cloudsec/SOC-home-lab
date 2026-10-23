# 📝 Document 

- **Failed Login alert generate on - Timestamp: October 20, 2026, 3:50:56 PM**
- **Severity: Medium**
- **Target Computer: DESKTOP-F0P06SK**
- **IP Address: 192.168.1.24**
- ---
- **First seen: Oct 20, 2026, 3:51:56.525 PM**
- **Account: Admin**
- **EventID: 4624 (Successful Logins)**
- **TotalEvents: 8**
- **Workstation Name: KALI**
- **Authentication Package: NTLM**
- **Logon Type: 3 (Network)**
- **TimeStamp: Oct 20,2026, 3:51:56.537 PM**
- **EventID: 5140 (Network Shared network)**
- **SharedName:ADMIN**
- **AccessMask: 0x1 (Read a Shared file)**


## 🛡️ Recommended Mitigations

- Restrict SMB share access using least-privilege permissions.

- Avoid storing passwords in plaintext.

- Use a password manager or an approved secrets-management solution.

- Rotate any real credentials that may have been exposed.

- Audit SMB access and file-transfer activity.
