# Scenario 2: Office Application Spawning Command Shell

## Initial Observation
An Office application initiated a command-line process,
indicating possible malicious macro or user-assisted execution.

## Event Correlation

### Event 1 – Process Creation (Sysmon Event ID 1)
- Parent Process: outlook.exe
- Child Process: cmd.exe
- User: LAB\Administrator
- Integrity Level: High

### Event 2 – Network Activity (Sysmon Event ID 3)
- Process: cmd.exe
- External network connection initiated

## Analyst Reasoning
Office applications should not spawn command shells.
This behavior strongly suggests a LOLBin execution technique
often associated with phishing-based attacks.

## Tier-1 Classification
Incident

## Response Actions
- Isolate endpoint if required
- Review email artifacts
- Preserve process evidence

## Escalation Decision
Immediate escalation to Tier-2.