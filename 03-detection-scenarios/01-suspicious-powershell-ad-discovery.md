# Scenario 1: Suspicious PowerShell LDAP Activity

## Initial Observation
A PowerShell process was launched from an unusual parent application
under an administrative user context.

## Event Correlation

### Event 1 – Process Creation (Sysmon Event ID 1)
- Parent Process: wordpad.exe
- Child Process: powershell.exe
- User: LAB\Administrator
- Integrity Level: High

### Event 2 – Network Connection (Sysmon Event ID 3)
- Process: powershell.exe
- Destination Port: 389 (LDAP)
- Destination Host: SRV1.lab.loc

## Analyst Reasoning
WordPad spawning PowerShell is not expected behavior.
The subsequent LDAP connection indicates potential Active Directory
enumeration using living-off-the-land techniques.

## Tier-1 Classification
Incident

## Response Actions
- Capture full command line
- Identify scope of LDAP queries
- Correlate with Security logs (4624 / 4672)

## Escalation Decision
Escalate to Tier-2 SOC for deeper investigation.