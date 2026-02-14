# Best Practices Guide

## Overview

This guide provides operational best practices for running SentinelMCP effectively, organized by workflow and responsibility layer.

---

## Alert Handling

Effective alert handling ensures rapid detection response and prevents false positives from consuming resources:

- **Route alerts to appropriate tier based on severity** - Use the alert severity score and threat intelligence context to determine which tier should handle the alert
- **Enrich with context before escalation** - Gather initial context (user info, asset details, threat intelligence) to inform escalation decisions
- **Track investigation progress and timeline** - Maintain a clear audit trail of all investigation steps and decision points
- **Document decisions and findings** - Record why escalations occurred, what was found, and outcomes

**Key Metrics:**

- Time from alert to triage decision
- False positive rate
- Escalation rate by severity

---

## Investigation

Structured investigation methodology ensures quality findings and proper evidence handling:

- **Use consistent data collection methods** - Apply standardized queries and collection procedures across Tier 2 investigations
- **Maintain chain of custody for evidence** - Document all evidence collected, who accessed it, and when
- **Document all findings and conclusions** - Create detailed investigation reports with supporting evidence
- **Escalate when scope grows beyond tier capability** - Recognize complexity signals that require Tier 3 forensic analysis

**Chain of Custody Template:**

- Evidence ID
- Collection date/time
- Collected by (agent name, analyst)
- Evidence location and accessibility
- All access and modifications

---

## Forensic Analysis

Deep forensic investigation follows legal and technical standards:

- **Collect all relevant evidence** - Comprehensive collection of logs, artifacts, network captures, and memory dumps
- **Preserve integrity of evidence** - Follow forensic principles to avoid contamination or modification
- **Follow legal requirements** - Ensure chain of custody and evidence handling comply with applicable regulations
- **Provide detailed root cause analysis** - Determine how the incident occurred, not just that it occurred

**Forensic Investigation Steps:**

1. Preserve evidence in original state
2. Document system configuration and state
3. Analyze evidence for root cause
4. Correlate findings across system components
5. Generate comprehensive forensic report

---

## Cloud Hunting

Proactive threat hunting identifies emerging threats before they escalate:

- **Run continuous anomaly detection** - Execute regular anomaly detection queries across cloud infrastructure
- **Correlate findings across accounts** - Connect related findings across multiple cloud accounts and subscriptions
- **Enrich with threat intelligence** - Supplement findings with external threat context and indicators
- **Feed findings to investigation tier** - Escalate promising leads to Tier 2 for formal investigation

**Hunting Priorities:**

1. Privileged account anomalies
2. Lateral movement indicators
3. Data exfiltration patterns
4. Configuration changes on critical resources
5. Authentication anomalies

---

## SLA Management

Maintaining SLA targets ensures timely responses to threats:

### SLA Response Times

| Severity     | Tier 1 Triage | Tier 2 Investigate | Tier 3 Forensic | Cloud Hunting |
| ------------ | ------------- | ------------------ | --------------- | ------------- |
| **Critical** | 5 min         | 30 min             | 8 hours         | 4 hours       |
| **High**     | 15 min        | 60 min             | 16 hours        | 4 hours       |
| **Medium**   | 30 min        | 2 hours            | 24 hours        | 4 hours       |
| **Low**      | 1 hour        | 4 hours            | 48 hours        | 4 hours       |

**SLA Escalation Rules:**

- Alert approaching SLA threshold → Escalate to next tier
- SLA breach → Management notification required
- Repeated breaches → Review tier capacity and staffing

---

## Quality Assurance

Maintain investigation quality through regular reviews:

- Document all assumptions and evidence sources
- Cross-validate findings with multiple data sources
- Peer review complex or high-severity cases
- Conduct post-incident reviews for lessons learned
- Track metrics: accuracy, SLA compliance, false positive rate

---

## Related Documentation

- [TIER_INTEGRATION.md](../../TIER_INTEGRATION.md) - Escalation framework
- [OPERATIONS/README.md](./README.md) - Operations procedures overview
- [CONTRIBUTING.md](../../CONTRIBUTING.md) - Contribution guidelines
