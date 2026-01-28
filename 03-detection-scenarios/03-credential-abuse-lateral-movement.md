# Scenario 3: Credential Abuse and Lateral Movement

## Initial Observation
Authentication activity was detected between internal hosts
using NTLM authentication, followed by privileged access
and lateral network movement.

The activity originated from a workstation and targeted
a domain resource, raising suspicion of credential misuse.

---

## Event Correlation

### Event 1 – Successful Logon (Security Event ID 4624)
- Logon Type: 3 (Network)
- Authentication Package: NTLM
- Account: Domain User
- Source Host: PC1.lab.loc
- Target Host: SRV1.lab.loc

Network logon using NTLM instead of Kerberos is notable,
especially when observed outside of expected service behavior.

---

### Event 2 – Privileged Logon (Security Event ID 4672)
- Account: Domain User
- Assigned Privileges: SeDebugPrivilege, SeTcbPrivilege

The account received special privileges shortly after
authentication, indicating elevated access.

---

### Event 3 – Network Connection (Sysmon Event ID 3)
- Process: `lsass.exe`
- Destination: `CIFS / SMB (Port 445)`
- Destination Host: DC1.lab.loc
- Initiated: Yes

The access pattern indicates potential credential reuse
to access administrative network resources.

---

## Analyst Reasoning
The combination of:
- NTLM-based authentication
- Network logon (Type 3)
- Privilege assignment shortly after logon
- SMB access to a domain controller or server

strongly suggests credential abuse rather than
legitimate user activity.

This behavior aligns with common lateral movement
techniques such as:
- Pass-the-Hash
- Token reuse
- Unauthorized service access

The absence of interactive logon and the use of NTLM
further reduce the likelihood of benign behavior.

---

## Tier-1 Classification
**Incident**

This activity qualifies as an Incident due to:
- Credential-based authentication abuse
- Privileged access escalation
- Lateral movement toward critical assets

---

## Response Actions
- Identify the source account and workstation
- Verify if NTLM authentication is expected in this environment
- Review additional authentication attempts from the same source
- Correlate with:
  - Event ID 4625 (Failed Logons)
  - Event ID 4769 (Kerberos Service Tickets)
- Check for similar access patterns across other hosts

---

## Escalation Decision
Escalate to **Tier-2 SOC** immediately.

Justification:
- High confidence credential misuse
- Potential compromise of privileged credentials
- Risk of further lateral movement or persistence

---

## Incident Documentation

This activity was documented using the SOC Tier-1 Incident Report template:

→ `05-incident-templates/tier1-incident-report.md`

The incident report includes:
- Authentication timeline
- Privilege escalation indicators
- Lateral movement evidence
- Impact assessment and escalation rationale
