# Sysmon Overview

Sysmon is used to enhance endpoint visibility beyond standard Windows Security logs.

## Data Sources Used
- Event ID 1 – Process Creation
- Event ID 3 – Network Connection

## Why Sysmon Matters
Sysmon provides:
- Parent-child process relationships
- Command-line visibility
- Network activity tied to a specific process

This context allows faster triage and more confident classification
(Noise / Exposure / Incident).