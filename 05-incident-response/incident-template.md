# SOC Tier-1 Incident Report

## 1. Executive Summary
High-level summary of the event, written so that a Tier-2 analyst
can understand the situation within 30 seconds.

Include:
- What was observed
- Why it matters
- Current status

---

## 2. Initial Detection
How the activity was identified.

Examples:
- SIEM alert
- Manual log review
- Sysmon correlation
- User report

Include timestamp and data source.

---

## 3. Evidence Collected

### Authentication Indicators
- Relevant Windows Security Event IDs (e.g. 4624, 4625, 4769)
- Logon type and authentication package
- Source IP / host

### Process & Host Indicators
- Sysmon Event IDs (e.g. ID 1, ID 3)
- Parent and child process relationships
- Command-line arguments
- Integrity level and user context

### Network Indicators
- Destination IP / hostname
- Port and protocol
- Direction (inbound / outbound)
- Purpose of connection (if known)

---

## 4. Event Timeline
Chronological sequence of relevant events.

Example format:
- T0 – Initial suspicious process execution
- T1 – Network connection to internal resource
- T2 – Authentication success using NTLM

---

## 5. Classification
**Noise / Exposure / Incident**

Final classification based on observed behavior,
context, and correlation results.

---

## 6. Analyst Assessment
Analyst reasoning behind the classification decision.

Address:
- Why this behavior is abnormal
- Whether attacker intent is suspected or confirmed
- Whether progression or impact is observed

This section reflects analytical judgment, not raw logs.

---

## 7. Impact Assessment
Evaluate potential impact:
- User accounts affected
- Systems involved
- Risk to identity, data, or lateral movement

If impact is unclear, state assumptions explicitly.

---

## 8. Recommended Actions
Immediate actions recommended at Tier-1 level.

Examples:
- Preserve logs and evidence
- Monitor for follow-up activity
- Isolate endpoint (if applicable)

---

## 9. Escalation Recommendation
Clear guidance for Tier-2.

Include:
- Why escalation is required
- What Tier-2 should focus on next
- Any unanswered questions or risks

---

## 10. Analyst Notes
Optional notes for internal SOC communication.

Used to document uncertainty, assumptions,
or items requiring confirmation.