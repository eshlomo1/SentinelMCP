# Operations Documentation

Complete operational procedures for running SentinelMCP MDR operations.

## Overview

This directory contains day-to-day operational guidance for security analysts, investigators, and forensic analysts across all tiers.

## Quick Navigation

### For Tier 1 Analysts

- [Tier 1 Operations](TIER1_OPERATIONS.md) - Alert triage and routing procedures
- [Escalation Checklist](ESCALATION_CHECKLIST.md) - When and how to escalate
- [Quick Reference](../REFERENCE/QUICK_REFERENCE.md) - 2-minute answers
- [Best Practices](BEST_PRACTICES.md) - Operational best practices

### For Tier 2 Investigators

- [Investigation Workflow](INVESTIGATION_WORKFLOW.md) - Step-by-step procedures
- [Tier Integration](TIER_INTEGRATION.md) - Escalating to Tier 3
- [Data Sources Guide](DATA_SOURCES.md) - Available evidence
- [Best Practices](BEST_PRACTICES.md) - Operational best practices

### For Tier 3 Forensic Analysts

- [Forensic Procedures](FORENSIC_PROCEDURES.md) - Evidence collection standards
- [Case Management](CASE_MANAGEMENT.md) - Case documentation
- [Chain of Custody](CHAIN_OF_CUSTODY.md) - Legal requirements
- [Best Practices](BEST_PRACTICES.md) - Operational best practices

## Files in This Directory

| File                        | Purpose                        | Audience             |
| --------------------------- | ------------------------------ | -------------------- |
| `BEST_PRACTICES.md`         | Best practices guide           | All tiers            |
| `TIER_INTEGRATION.md`       | Automatic escalation framework | All tiers            |
| `TIER1_OPERATIONS.md`       | Alert handling procedures      | Tier 1 analysts      |
| `INVESTIGATION_WORKFLOW.md` | Investigation procedures       | Tier 2 investigators |
| `FORENSIC_PROCEDURES.md`    | Evidence collection            | Tier 3 analysts      |
| `DATA_SOURCES.md`           | Available data sources         | All investigators    |
| `ESCALATION_CHECKLIST.md`   | Quick escalation guide         | All tiers            |
| `CASE_MANAGEMENT.md`        | Case documentation             | Tier 2 & 3           |
| `CHAIN_OF_CUSTODY.md`       | Legal evidence handling        | Tier 3               |

## SLA Response Times

| Severity    | Tier 1 | Tier 2  | Tier 3   |
| ----------- | ------ | ------- | -------- |
| 🔴 Critical | 30 sec | 5 min   | 1 hour   |
| 🟠 High     | 2 min  | 15 min  | 4 hours  |
| 🟡 Medium   | 5 min  | 30 min  | 8 hours  |
| 🟢 Low      | 15 min | 4 hours | 24 hours |

## Common Workflows

### Alert Processing (Tier 1)

1. **Receive** → Alert ingestion from data sources
2. **Normalize** → Standardize alert format
3. **Enrich** → Add context and threat intelligence
4. **Route** → Determine appropriate destination
5. **Decide** → Route to Tier 2 or close as false positive

**SLA:** 5-15 minutes depending on severity

### Investigation (Tier 2)

1. **Analyze** → Collect evidence and determine scope
2. **Assess** → Evaluate threat and impact
3. **Escalate?** → Determine if Tier 3 investigation needed
4. **Report** → Document findings
5. **Close** → Archive or escalate

**SLA:** 30-60 minutes depending on severity

### Forensic Analysis (Tier 3)

1. **Collect** → Gather all evidence
2. **Preserve** → Maintain chain of custody
3. **Analyze** → Deep technical investigation
4. **Document** → Complete forensic report
5. **Close** → Case closure with remediation plan

**SLA:** 8-24 hours depending on severity

## Escalation Framework

See [TIER_INTEGRATION.md](TIER_INTEGRATION.md) for:

- Automatic escalation triggers
- Manual escalation procedures
- Conditional escalation criteria
- SLA requirements
- Authority and approval flows

## Support

- Questions? Check [FAQ](../FAQ.md)
- Need definitions? See [Glossary](../GLOSSARY.md)
- Having issues? See [Troubleshooting](../SUPPORT/TROUBLESHOOTING.md)

---

**Last Updated**: February 14, 2026 | **Version**: 1.0.2
