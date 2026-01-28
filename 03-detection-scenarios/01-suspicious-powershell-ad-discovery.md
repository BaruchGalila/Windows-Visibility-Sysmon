# Scenario 1: Suspicious PowerShell LDAP Activity

## Initial Observation
A PowerShell process was launched from an unusual parent application
under an administrative user context.

This activity was detected during routine Sysmon log review
focused on identifying abnormal parent-child process relationships.

---

## Event Correlation

### Event 1 – Process Creation (Sysmon Event ID 1)
- Parent Process: `wordpad.exe`
- Child Process: `powershell.exe`
- User: `LAB\Administrator`
- Integrity Level: High

This parent-child relationship is highly unusual and not consistent
with expected Windows behavior.

---

### Event 2 – Network Connection (Sysmon Event ID 3)
- Process: `powershell.exe`
- Destination Host: `SRV1.lab.loc`
- Destination Port: `389` (LDAP)
- Protocol: TCP

The LDAP connection indicates potential Active Directory enumeration
or discovery activity originating from the PowerShell session.

---

## Analyst Reasoning
WordPad spawning PowerShell is not expected behavior and represents
a classic Living-Off-The-Land (LOLBin) execution pattern.

The immediate LDAP connection to a domain controller suggests
identity reconnaissance or directory enumeration rather than
legitimate administrative activity.

The combination of:
- Abnormal parent-child relationship
- Elevated privileges
- Direct LDAP communication

raises the confidence level of malicious intent.

---

## Tier-1 Classification
**Incident**

This activity exceeds Exposure level due to:
- Execution under administrative context
- Active interaction with domain infrastructure
- Clear deviation from baseline behavior

---

## Response Actions
- Capture full PowerShell command line arguments
- Identify scope and volume of LDAP queries
- Correlate with Windows Security logs:
  - Event ID 4624 (Successful Logon)
  - Event ID 4672 (Special Privileges Assigned)
- Check for similar behavior across other endpoints

---

## Escalation Decision
Escalate to **Tier-2 SOC** for advanced investigation and containment.

This escalation is justified due to:
- High-confidence LOLBin execution
- Potential credential or directory abuse
- Domain-level impact risk

---

## Incident Documentation

This activity was documented using the SOC Tier-1 Incident Report template:

→ `05-incident-templates/tier1-incident-report.md`

The incident report includes:
- Event correlation summary
- Classification rationale
- Timeline of activity
- Impact assessment
- Escalation justification
