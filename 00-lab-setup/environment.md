# Lab Environment Details

This document provides the technical context required to understand
the logs, scenarios, and investigations performed in this project.

It is written from a SOC Tier-1 perspective.

---

## Operating System

- Windows 10 (x64)
- Fully patched
- Local Administrator account used for controlled testing
- Endpoint monitored using Sysmon

---

## Sysmon Configuration Context

- Sysmon is installed as a persistent service
- Focused on high-signal events relevant to investigation:
  - Process creation
  - Network connections
- The configuration prioritizes **clarity over volume**

(Sysmon configuration details are documented separately under `/01-sysmon`)

---

## Logging Scope

### Endpoint Telemetry
- Sysmon Operational Log
  - Event ID 1: Process Create
  - Event ID 3: Network Connection

### Identity / Security Context
- Windows Security Event Log (when correlated)
  - Authentication context
  - Privilege level validation

---

## Network Context

- Internal lab network
- No exposure to production systems
- All IP addresses observed belong to the lab subnet
- External connections (when present) are simulated and controlled

---

## Assumptions for Investigation

- All events are analyzed as if they were received by a SOC
- The analyst does not assume malicious intent by default
- Classification is based on:
  - Behavior
  - Sequence
  - Context
  - Privilege

---

## What This Environment Is NOT

- Not a penetration testing lab
- Not malware development
- Not exploitation-focused

The purpose is **visibility, reasoning, and decision-making**.