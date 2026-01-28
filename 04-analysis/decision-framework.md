# Tier-1 Decision Framework

## Classification Philosophy
Event classification is not binary.
It exists on a spectrum.

The analyst’s task is to determine
where the activity falls on that spectrum.

## Noise
Expected behavior that:
- Matches baseline activity
- Has a clear business or system explanation
- Does not introduce risk

No further action required.

## Exposure
Suspicious or abnormal behavior that:
- Shows deviation from baseline
- Lacks confirmation of success
- Requires monitoring and enrichment

Documented and tracked for escalation if behavior continues.

## Incident
Confirmed or high-confidence malicious behavior that:
- Demonstrates attacker progression
- Shows privilege abuse or lateral movement
- Impacts authentication, identity, or network trust

Immediate escalation to Tier-2 is required.

## Guiding Rule
If intent and impact are both present —
it is an Incident.

If intent is suspected but impact is unclear —
it is an Exposure.