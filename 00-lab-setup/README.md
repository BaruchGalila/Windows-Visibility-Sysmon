# Lab Setup (Windows Visibility + Sysmon)

This project runs in an isolated lab environment designed to simulate realistic Tier-1 SOC investigations using endpoint telemetry (Sysmon) and Windows logs.

The purpose of this lab is **defensive visibility**:
- Collect high-fidelity endpoint events
- Correlate them into investigation timelines
- Practice Tier-1 triage and escalation-ready documentation

---

## Environment Overview

**Endpoint (Victim / Telemetry Source)**
- Windows 10 (domain-joined in my AD lab / or standalone depending on the scenario)

**Domain Services (when applicable)**
- Windows Server (AD DS / DNS / Kerberos)

**Attacker Simulation (isolated lab only)**
- Kali Linux or controlled “malicious-like” execution from the endpoint itself (LOLBins)

**Network**
- Internal lab subnet (no production exposure)

---

## Data Sources Used

This project relies on two main log sources:

### 1) Sysmon (Primary Telemetry)
Used for high-context endpoint visibility:
- Parent → child process chains
- Command line and image path
- Network connections tied to a process
- Hashes (when enabled)

### 2) Windows Security Logs (Validation / Identity Context)
Used to validate identity + authentication context:
- Successful/failed logons
- Privilege assignments
- Lateral movement indicators (where applicable)

---

## Assumptions and Scope

- All activity is generated in a controlled lab for learning purposes.
- This repository focuses on **how events look and how to reason about them** (Tier-1), not exploitation.
- Any “attack-like” behavior is performed only to produce telemetry and practice investigation.

---

## Why This Setup Matches Tier-1 SOC Work

Tier-1 analysts rarely get a perfect alert.
They get fragments: a process, a user, an IP, a timestamp.

This lab is built to practice exactly that:
- Start from a suspicious endpoint signal (Sysmon)
- Enrich it with identity/auth logs (Security)
- Decide: **Noise / Exposure / Incident**
- Document clearly and escalate when necessary