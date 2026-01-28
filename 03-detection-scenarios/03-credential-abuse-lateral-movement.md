# Scenario 3: Credential Abuse and Lateral Movement

## Initial Observation
A privileged process initiated authenticated network access
to a domain server using non-interactive logon behavior.

## Event Correlation

### Event 1 – Process Execution (Sysmon Event ID 1)
- Process: powershell.exe
- User: LAB\Administrator
- Integrity Level: High

### Event 2 – Network Connection (Sysmon Event ID 3)
- Destination Host: DC.lab.loc
- Destination Port: 445 (SMB)

## Analyst Reasoning
Administrative PowerShell activity combined with SMB access
may indicate credential abuse or lateral movement.
Such activity requires immediate validation.

## Tier-1 Classification
Incident

## Response Actions
- Correlate with Security logs (4624 Logon Type 3)
- Identify authentication method (NTLM / Kerberos)
- Assess lateral movement scope

## Escalation Decision
Escalate to Tier-2 for credential compromise investigation.