# Analyst Reasoning & Conclusions

## Investigation Mindset
The investigation does not begin with a single alert,
but with understanding *context*.

The primary goal is to determine whether observed activity
aligns with expected operating system behavior,
user intent, and environmental norms.

Rather than asking *“Is this malicious?”*,
the analyst asks:
- *Does this behavior make sense in this environment?*
- *Is the sequence of events logical?*
- *Is the privilege level justified?*

## Analytical Approach
The analysis follows a layered methodology:

1. **Process Lineage**
   - Examine parent-child relationships
   - Identify abnormal execution chains (e.g. Office → PowerShell)

2. **Temporal Correlation**
   - Validate the order of events
   - Determine whether execution, authentication, and network activity
     form a meaningful sequence

3. **Privilege Context**
   - Assess whether elevated privileges are expected
   - Pay special attention to high-integrity or administrative execution

4. **Network Impact**
   - Correlate host behavior with outbound or lateral network connections
   - Identify access to sensitive services (LDAP, SMB, RPC)

## Decision Framework
Event classification is not binary.
It is the result of accumulated signals.

Classification is based on:
- Behavioral deviation from baseline
- Execution context
- Privilege abuse potential
- Network reach and impact

A single indicator may justify **Exposure**.
Multiple aligned indicators justify an **Incident**.

## Core SOC Principle
Individual events are noise.

Meaning emerges only through correlation.

Detection is not about spotting anomalies —
it is about understanding patterns, intent,
and operational risk.