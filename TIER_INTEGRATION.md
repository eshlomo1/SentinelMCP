# MDR Tier Integration & Escalation Framework

**Last Updated**: February 14, 2026  
**Version**: 1.0  
**Organization**: PurpleX Lab  
**Framework**: Sentinel MCP

## Overview

The Sentinel MCP framework includes three investigation tiers with clear escalation paths and decision criteria. This document describes the integration between tiers and when incidents escalate from one tier to the next.

---

## Quick Reference: Escalation Path

```
Initial Alert
    ↓
TIER 1: Triage & Normalization
    ↓
    ├─→ [False Positive] → Archive
    ├─→ [Low Severity] → Batch Review
    ├─→ [Medium Severity] → Tier 1 Investigation
    │   └─→ [Investigation reveals compromise] → Escalate to TIER 2
    └─→ [High/Critical OR Evidence of Compromise] → Escalate to TIER 2
          ↓
    TIER 2: Investigation & Analysis
          ↓
          ├─→ [False Positive] → Close
          ├─→ [Suspicious but unconfirmed] → Continue monitoring
          └─→ [Confirmed Incident] → [Need forensic analysis?]
              └─→ [Yes] → Escalate to TIER 3
                    ↓
          TIER 3: Forensic Analysis
                    ↓
                    └─→ [Root Cause Determined] → Close & Report
```

---

## TIER 1 → TIER 2 ESCALATION

### Automatic Escalation Triggers

These conditions **automatically trigger** escalation to Tier 2:

| #   | Condition                        | Description                              | Response SLA      | Examples                                                        |
| --- | -------------------------------- | ---------------------------------------- | ----------------- | --------------------------------------------------------------- |
| 1   | **CRITICAL_SEVERITY**            | Alert marked as CRITICAL                 | Immediate (5 min) | Critical code execution, active C2 communication                |
| 2   | **CONFIRMED_COMPROMISE**         | 3+ compromise indicators detected        | Immediate (5 min) | File replaced + registry modified + scheduled task + network C2 |
| 3   | **HIGH_SEVERITY_WITH_EVIDENCE**  | High alert + 2+ context indicators       | 1-4 hours         | High-risk malware + anomalous network traffic                   |
| 4   | **LATERAL_MOVEMENT_DETECTED**    | Lateral movement or privilege escalation | 10 minutes        | Multiple failed auth attempts + admin privilege acquisition     |
| 5   | **MULTIPLE_CORRELATED_ALERTS**   | 5+ related alerts within 1 hour          | 30 minutes        | Same source, escalating severity pattern                        |
| 6   | **DATA_EXFILTRATION_INDICATORS** | Evidence of data exfiltration            | 5 minutes         | Large transfer to external IP + encryption + file compression   |

### Manual Escalation

Tier 1 analyst can manually escalate with documentation:

- **Analyst Judgment**: Analyst determines escalation warranted
  - Must document reasoning
  - Must provide supporting evidence
  - Escalates immediately upon request

### Conditional Escalation (During Tier 1 Investigation)

- **MEDIUM_SEVERITY_AFTER_INVESTIGATION**: If Tier 1 investigation reveals compromise indicators
- **PATTERN_CORRELATION_DETECTED**: If correlation analysis identifies attack pattern

### Escalation Process (Tier 1 → Tier 2)

```
Step 1: Decision Point
   ↓ AlertRouter evaluates criteria
Step 2: Escalation Approval
   ↓ Automatic (or analyst approval for manual)
Step 3: Case Creation
   ↓ Investigation case created with all evidence
Step 4: Tier 2 Assignment
   ↓ Route to appropriate specialist(s)
Step 5: Notification
   ↓ Email + Slack to Tier 2 team
Step 6: SLA Clock Starts
   ↓ Tier 2 has 5-30 min to respond (based on severity)
```

### Key Information Handed Off

- Normalized alert data
- Enrichment context (threat intel, asset info)
- Supporting evidence artifacts
- Escalation reason clearly documented
- Tier 1 findings and observations

---

## TIER 2 → TIER 3 ESCALATION

### Automatic Escalation Triggers

These conditions **automatically trigger** escalation to Tier 3 (Forensic):

| #   | Condition                          | Description                                   | Response SLA | Examples                                                        |
| --- | ---------------------------------- | --------------------------------------------- | ------------ | --------------------------------------------------------------- |
| 1   | **CONFIRMED_INCIDENT_WITH_IMPACT** | Incident confirmed + data/systems compromised | Immediate    | Verified data exfiltration or 3+ systems affected               |
| 2   | **ADVANCED_PERSISTENT_THREAT**     | APT or sophisticated attacker indicators      | 30 minutes   | Custom malware + anti-analysis + living-off-land techniques     |
| 3   | **SUSPECTED_RANSOMWARE**           | Ransomware deployment or testing evidence     | 10 minutes   | Mass file encryption + MBR modification + ransom note           |
| 4   | **INSIDER_THREAT_CONFIRMED**       | Internal malicious actor confirmed            | 30 minutes   | Privileged account abuse by employee + unauthorized data access |
| 5   | **EVIDENCE_CHAIN_REQUIRED**        | Legal/regulatory requirements active          | 1 hour       | Legal hold initiated or incident response plan activated        |
| 6   | **UNKNOWN_PERSISTENCE**            | Attacker persistence mechanism unidentified   | 2-4 hours    | Persistence confirmed but method cannot be identified           |
| 7   | **INCOMPLETE_LATERAL_MOVEMENT**    | Full extent of lateral movement unknown       | 2-4 hours    | Lateral movement detected, scope unclear                        |

### Manual Escalation

Tier 2 coordinator (Threat Assessor) can escalate based on investigation findings:

- **Tier 2 Recommendation**: Investigator determines forensic analysis necessary
  - Must provide complete investigation findings
  - Must justify why Tier 3 analysis needed
  - Must document evidence and hypotheses to test

### Conditional Escalation (During Tier 2 Investigation)

- **STALLED_INVESTIGATION**: Investigation cannot proceed without forensic analysis
- **FORENSIC_REQUIREMENTS**: Evidence integrity or legal proceedings require forensic chain of custody

### Escalation Process (Tier 2 → Tier 3)

```
Step 1: Investigation Conclusion
   ↓ ThreatAssessor completes investigation
Step 2: Escalation Decision
   ↓ Evaluate escalation criteria against findings
Step 3: Evidence Preservation
   ↓ Stop investigation, snapshot system state
Step 4: Forensic Case Creation
   ↓ Create forensic case with evidence manifest
Step 5: Tier 3 Assignment
   ↓ Route to forensic specialists
Step 6: Notification
   ↓ Email + Slack + Phone to Tier 3 team
Step 7: Forensic SLA Clock Starts
   ↓ Tier 3 has 4-24 hours to begin analysis (based on severity)
```

### Key Information Handed Off

- Complete Tier 2 investigation report
- All evidence artifacts and hashes
- Evidence manifest and integrity validation
- Chain of custody documentation (signed)
- Preliminary timeline of events
- Hypotheses to test in forensic analysis
- List of systems/users to analyze
- Legal/regulatory requirements

---

## Escalation Authority

### Tier 1 Escalation Authority

- **Agent**: Tier1-AlertRouter
- **Authority**: Unilateral escalation to Tier 2 based on defined criteria
- **Override**: Manual escalation request from Tier 1 analyst

### Tier 2 Escalation Authority

- **Agent**: Tier2-ThreatAssessor (coordinator)
- **Authority**: Escalation to Tier 3 based on investigation findings
- **Override**: Manual decision by Tier 2 lead

### Tier 3 Final Authority

- **Agent**: Tier3-RootCauseAnalyzer (case lead)
- **Authority**: Case closure and final determination
- **Responsibility**: No further escalation; final investigation authority

---

## Escalation SLAs by Severity

### Tier 1 → Tier 2 Response Times

| Severity     | Decision SLA | Escalation SLA                   | Notes                                |
| ------------ | ------------ | -------------------------------- | ------------------------------------ |
| **CRITICAL** | 2 minutes    | Immediate (0-5 min)              | Automatic + leadership notification  |
| **HIGH**     | 5 minutes    | 1-4 hours                        | Automatic queue to investigation     |
| **MEDIUM**   | 10 minutes   | 2-4 hours after T1 investigation | Only if investigation reveals issues |
| **LOW**      | 30 minutes   | Pattern-dependent                | Batch processing typical             |

### Tier 2 → Tier 3 Response Times

| Severity              | Decision SLA            | Begins SLA                          | Notes                              |
| --------------------- | ----------------------- | ----------------------------------- | ---------------------------------- |
| **CRITICAL INCIDENT** | 2 hours investigation   | 4 hours to begin forensic analysis  | All resources engaged              |
| **HIGH PRIORITY**     | 4-8 hours investigation | 8 hours to begin forensic analysis  | Standard investigation tempo       |
| **MEDIUM PRIORITY**   | 24 hours investigation  | 24 hours to begin forensic analysis | Can wait for forensic availability |

---

## Integration Points

### Case Management

Every incident follows a **case ID** (INC-YYYY-#####) from Tier 1 through Tier 3:

- **Tier 1 Owner**: Tier1-AlertRouter (creates case)
- **Tier 2 Owner**: Tier2-ThreatAssessor (takes ownership at escalation)
- **Tier 3 Owner**: Tier3-RootCauseAnalyzer (takes ownership at escalation)

### Communication Channels

**Tier 1 → Tier 2**:

- Email: tier1-escalations@purplexlab.com → tier2-team@purplexlab.com
- Slack: #tier1-escalations
- Case system: Investigation case ticket

**Tier 2 → Tier 3**:

- Email: tier2-escalations@purplexlab.com → tier3-forensic@purplexlab.com
- Slack: #tier2-escalations
- Case system: Forensic case ticket

---

## Performance Metrics

### Escalation Volume

- **Tier 1 → Tier 2**: Target 15-25% of alerts escalated
- **Tier 2 → Tier 3**: Target 5-10% of investigations escalated

### SLA Compliance

- **Tier 1 Decision**: Target 95% within SLA
- **Tier 2 Decision**: Target 95% within SLA
- **Tier 3 Start**: Target 90% within SLA

### False Positive Rates

- **Tier 1**: Target < 15% escalated as FP
- **Tier 2**: Target < 5% escalated as FP

---

## Escalation Criteria Examples

### Example 1: Automatic Tier 1 → Tier 2

**Scenario**: Malware detection alert (HIGH severity)

1. **Alert Received**: Suspicious .exe file detected with hash not in whitelist
2. **Tier 1 Processing**:
   - AlertParser: Normalizes alert from Defender
   - AlertEnricher: Looks up file hash in threat intel → **Known malware**
   - AlertRouter: Evaluates criteria
     - Severity = HIGH ✓
     - Threat intel match = malware ✓
     - **Escalation Criteria Met** → Automatically escalate
3. **Escalation to Tier 2**:
   - Case created: INC-2026-00542
   - Routed to Tier2-MalwareAnalyzer (+ others)
   - Tier 2 begins analysis within 15 minutes

---

### Example 2: Conditional Tier 1 → Tier 2

**Scenario**: Medium severity alert, investigation reveals more

1. **Alert Received**: Minor network anomaly (MEDIUM severity)
2. **Tier 1 Processing**:
   - AlertRouter routes to Tier 1 investigation queue
   - Tier 1 investigates for 30 minutes
   - **Finding**: The network anomaly correlates with 3 other alerts from same source
3. **Escalation Decision**:
   - Pattern detected (5 alerts from same source, escalating severity)
   - **Escalation triggered** (PATTERN_CORRELATION_DETECTED)
4. **Escalation to Tier 2**:
   - Case created: INC-2026-00543
   - Tier 2 investigates coordinated attack pattern
   - Full investigation scope determined by Tier 2

---

### Example 3: Automatic Tier 2 → Tier 3

**Scenario**: Investigation confirms data breach

1. **Tier 2 Investigation**:
   - MalwareAnalyzer: Confirms malware execution
   - NetworkInvestigator: Identifies C2 communication
   - IdentityAnalyzer: Detects credential theft
   - ThreatAssessor: Data exfiltration confirmed
2. **Escalation Criteria Met**:
   - CONFIRMED_INCIDENT_WITH_IMPACT ✓
   - Data compromised = verified ✓
   - Multiple indicators = 4+ ✓
3. **Escalation to Tier 3**:
   - Evidence preserved, investigation stopped
   - Forensic case created with evidence manifest
   - Routed to Tier 3 team (4-hour SLA to begin analysis)
   - Legal team notified due to data breach

---

### Example 4: Manual Tier 2 → Tier 3

**Scenario**: Suspicious activity, unclear origin

1. **Tier 2 Investigation** (incomplete):
   - Lateral movement confirmed but unknown mechanism
   - Attacker persistence suspected but not identified
   - Cannot determine full scope
2. **Escalation Decision** (Manual):
   - ThreatAssessor determines forensic analysis necessary
   - Cannot resolve without memory/disk forensics
   - **Requests Tier 3 escalation**
3. **Escalation to Tier 3**:
   - Case created with investigation findings
   - Forensic team begins memory/disk analysis
   - Tier 3 goal: Identify persistence and lateral movement method

---

## When NOT to Escalate

### At Tier 1

Do **NOT** escalate if:

- ✓ Confirmed false positive
- ✓ Known benign activity pattern
- ✓ Low severity with no indicators
- ✓ Resolved by Tier 1 investigation (low severity only)

### At Tier 2

Do **NOT** escalate if:

- ✓ Confirmed false positive after investigation
- ✓ Low/medium severity incident resolved
- ✓ No compromise evidence despite initial alerts
- ✓ Known legitimate activity (false positive identified)

---

## Override Procedures

### Security Leadership Override

- **Authority**: SOC Manager, Security Director
- **Action**: Can force escalation to any tier
- **Documentation**: Reason must be documented
- **Example**: CEO's device involved → Force to Tier 3

### Law Enforcement Trigger

- **Authority**: Law enforcement or legal department
- **Action**: Immediately escalate to Tier 3 with legal hold
- **Chain of Custody**: Strict forensic procedures activate
- **Notification**: CEO/General Counsel notified

### Incident Response Plan Activation

- **Authority**: Security Leadership
- **Action**: All tiers engaged simultaneously for critical incidents
- **Coordination**: IR coordinator becomes primary case owner
- **Model**: Parallel investigation across all tiers

---

## Related Documents

- [data/tier-integration.yaml](../data/tier-integration.yaml) - Technical escalation criteria and handoff procedures
- [agents/tier1-agents.yaml](../agents/tier1-agents.yaml) - Tier 1 agent definitions with escalation criteria
- [agents/tier2-agents.yaml](../agents/tier2-agents.yaml) - Tier 2 agent definitions with escalation criteria
- [agents/tier3-forensic-agents.yaml](../agents/tier3-forensic-agents.yaml) - Tier 3 agent definitions
- [data/escalation-paths.yaml](../data/escalation-paths.yaml) - Legacy escalation matrix
- [data/workflows.yaml](../data/workflows.yaml) - Operational workflows

---

**Document Version**: 1.0  
**Last Updated**: February 14, 2026  
**Prepared By**: PurpleX Lab Security Operations Team  
**Contact**: tier-integration@purplexlab.com
