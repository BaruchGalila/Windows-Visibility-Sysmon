# Raw Event Collection

This document contains **unaltered raw event samples**
used throughout the project.

No interpretation or classification is performed here.

---

## Sysmon Event ID 1 – Process Creation

Timestamp:
2026-01-08 11:24:43

Process:
powershell.exe

Parent Process:
wordpad.exe

User:
LAB\Administrator

Integrity Level:
High

Command Line:
"C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe"

---

## Sysmon Event ID 3 – Network Connection

Timestamp:
2026-01-08 11:25:55

Process:
powershell.exe

Destination:
192.168.56.10

Port:
389 (LDAP)

Initiated:
True

User:
LAB\Administrator

---

## Windows Security Event ID 4624 – Successful Logon

Logon Type:
3 (Network)

Authentication Package:
NTLM

User:
LAB\Administrator

Source IP:
192.168.56.11

---

## Notes

- Events are intentionally presented without conclusions
- Correlation and classification are performed in later stages
- This mirrors real SOC evidence handling