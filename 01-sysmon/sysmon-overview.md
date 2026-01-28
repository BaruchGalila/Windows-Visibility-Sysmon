# Sysmon Visibility Strategy

This document explains how Sysmon is used in this project
to enhance endpoint visibility from a SOC Tier-1 perspective.

Sysmon is treated as a **telemetry source**, not a detection engine.

---

## Why Sysmon Was Deployed

Native Windows Security logs often lack:
- Parent-child process relationships
- Full command-line visibility
- Process-linked network context

Sysmon bridges these gaps.

---

## Sysmon Event IDs Used

### Event ID 1 – Process Creation
Used to identify:
- Abnormal parent-child relationships
- Living-off-the-Land (LOLBin) execution
- Privileged process execution context

Key fields analyzed:
- ParentImage
- Image
- CommandLine
- IntegrityLevel
- User

---

### Event ID 3 – Network Connection
Used to:
- Tie network activity to a specific process
- Identify suspicious outbound connections
- Detect internal reconnaissance or lateral movement

Key fields analyzed:
- Image
- DestinationIp / DestinationPort
- Initiated
- User

---

## What Sysmon Is NOT Used For

- Not signature-based detection
- Not alerting
- Not IOC matching

All classification decisions are made by the analyst,
based on **correlation and context**.

---

## Analyst Mindset

Sysmon answers the question:
> “What actually happened on the endpoint?”

It does NOT answer:
> “Is this malicious?”

That decision belongs to the SOC analyst.

---

## Output of Sysmon in This Project

Sysmon events are:
- Collected
- Correlated
- Interpreted
- Documented

They are never treated in isolation.

This mirrors real SOC Tier-1 operations.