# Lab Environment Overview

This project was conducted in an isolated lab environment for defensive security learning.

## Environment Components
- Windows 10 endpoint with Sysmon installed
- Event Viewer (Microsoft-Windows-Sysmon/Operational)
- Windows Security Event Log
- No production systems involved

## Assumptions
- All activity is analyzed post-execution
- No automated detection or blocking
- Focus is on visibility, correlation, and analyst reasoning

## Analyst Perspective
All analysis is performed from a SOC Tier-1 / Security Tech Support viewpoint:
observe → correlate → classify → escalate