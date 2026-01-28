# Scenario 2: Office Application LOLBin Execution

## Initial Observation
An Office application initiated a command-line execution,
resulting in suspicious child process activity under an
administrative user context.

This behavior was detected during Sysmon-based review
focused on identifying abnormal application behavior
and Living-Off-The-Land techniques.

---

## Event Correlation

### Event 1 – Process Creation (Sysmon Event ID 1)
- Parent Process: `winword.exe`
- Child Process: `cmd.exe`
- User: `LAB\Administrator`
- Integrity Level: High

Microsoft Word should not normally spawn command-line
interpreters, especially under elevated privileges.

---

### Event 2 – Secondary Process Execution (Sysmon Event ID 1)
- Parent Process: `cmd.exe`
- Child Process: `powershell.exe`
- User: `LAB\Administrator`
- Integrity Level: High

The execution chain indicates command execution
originating from an Office document.

---

### Event 3 – Network Connection (Sysmon Event ID 3)
- Process: `powershell.exe`
- Destination: External IP address
- Protocol: TCP
- Connection Initiated: Yes

Outbound network communication following Office-based
execution significantly increases malicious confidence.

---

## Analyst Reasoning
Office applications spawning command-line interpreters
is a well-known malicious pattern commonly associated
with phishing-delivered payloads.

The execution chain:
`winword.exe → cmd.exe → powershell.exe`

combined with outbound network communication strongly
suggests Living-Off-The-Land abuse rather than legitimate
administrative activity.

This pattern is consistent with:
- Initial Access
- Execution
- Command-and-Control preparation

---

## Tier-1 Classification
**Incident**

This activity qualifies as an Incident due to:
- Clear LOLBin execution chain
- Elevated privileges
- External network communication
- High-risk attack pattern commonly used in real-world campaigns

---

## Response Actions
- Preserve the original Office document
- Capture full command-line arguments from Sysmon
- Identify destination IP reputation
- Correlate with Windows Security logs:
  - Event ID 4624 (Logon)
  - Event ID 4672 (Privilege Assignment)
- Check for similar execution patterns on other endpoints

---

## Escalation Decision
Escalate to **Tier-2 SOC** immediately.

Justification:
- High-confidence malicious execution
- Potential phishing-based initial access
- Risk of payload download or lateral movement

---

## Incident Documentation

This activity was documented using the SOC Tier-1 Incident Report template:

➡️ `05-incident-templates/tier1-incident-report.md`

The incident report includes:
- Execution chain analysis
- Evidence correlation
- Risk assessment
- Escalation rationale