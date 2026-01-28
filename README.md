# Windows Visibility & Investigation Lab (Sysmon)

A hands-on endpoint visibility and investigation project focused on **Sysmon-based telemetry**, designed from a **SOC Tier-1 / Security Technical Support perspective**.

This lab demonstrates how enhanced endpoint visibility enables accurate **triage, correlation, and incident classification**, beyond what standard Windows Security logs provide.

The project emphasizes **defensive investigation**, analytical thinking, and escalation-ready documentation — not exploitation.

---

## Project Objectives

This project was built to:

- Extend endpoint visibility beyond native Windows Security logs using Sysmon
- Analyze **parent-child process relationships** and execution context
- Correlate **process execution with network activity**
- Practice SOC Tier-1 classification:
  - Noise
  - Exposure
  - Incident
- Document findings using a **structured, escalation-ready workflow**
- Strengthen investigation intuition through real, correlated scenarios

---

## Lab Environment

- **Endpoint:** Windows 10 (Sysmon installed)
- **Log Source:** Microsoft-Windows-Sysmon/Operational
- **Tools:** Event Viewer, PowerShell
- **Scope:** Defensive analysis only
- **Perspective:** SOC Tier-1 / Security Technical Support

All activity was performed in an isolated lab environment.

---

## Project Structure

```text
Windows-Visibility-Sysmon/
├── 00-lab-setup/              Lab assumptions and environment description
├── 01-sysmon/                 Sysmon overview and visibility rationale
├── 02-event-collection/       Raw Sysmon event examples
├── 03-detection-scenarios/    Correlated investigation scenarios
├── 04-analysis/               Analyst reasoning and conclusions
└── 05-incident-templates/     SOC Tier-1 incident documentation templates
```

Each directory reflects a **real SOC investigation phase**, from raw telemetry to escalation.

---

## Detection Scenarios (Core of the Project)

The `03-detection-scenarios/` directory contains fully correlated investigation cases, each built from **multiple Sysmon events**.

### Scenarios Covered

1. **Suspicious PowerShell LDAP Activity**
   - Abnormal parent-child relationship
   - PowerShell execution under elevated context
   - LDAP network activity toward a domain server

2. **Office LOLBin Execution**
   - Office application spawning command-line tools
   - Living-off-the-land behavior
   - High-confidence malicious execution pattern

3. **Credential Abuse & Lateral Movement**
   - Credential misuse indicators
   - Network-based movement patterns
   - Privileged execution context

Each scenario includes:
- Initial observation
- Event correlation (Sysmon Event IDs 1 & 3)
- Analyst reasoning
- Tier-1 classification
- Response and escalation decision

---

## Investigation Methodology

The investigation approach throughout this project follows a Tier-1 SOC mindset:

- Identify abnormal execution context
- Validate behavior against expected OS behavior
- Correlate **process activity + network telemetry**
- Avoid single-event conclusions
- Classify based on **sequence, context, and impact**

> Single events rarely indicate compromise.  
> **Patterns do.**

---

## Incident Documentation

All incidents are documented using a reusable **SOC Tier-1 Incident Report Template**, including:

- Summary of activity
- Evidence and correlated events
- Classification rationale
- Analyst assessment
- Escalation recommendation

Template location:
05-incident-templates/
---

## Key Takeaways

This project demonstrates:

- Strong understanding of endpoint visibility concepts
- Practical Sysmon usage for SOC investigations
- Confident Tier-1 triage and classification
- Clear, escalation-ready documentation
- Analytical thinking rather than signature-based detection

---

## Disclaimer

This project was created strictly for **defensive security learning purposes**.  
All activity occurred in an isolated lab environment.