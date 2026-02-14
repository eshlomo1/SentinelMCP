# Sentinel MCP Hierarchy Summary

## Overview

A complete Sentinel MCP hierarchy has been created for PurpleX Lab's Microsoft Sentinel workspace, providing a structured approach to Managed Detection and Response (MDR) operations across four operational tiers:

- **Tier 1**: Alert triage, normalization, and routing (4 agents)
- **Tier 2**: In-depth investigation and threat assessment (4 agents)
- **Tier 3**: Forensic analysis and root cause determination (4 agents)
- **Cloud Threat Hunter**: Proactive cloud infrastructure hunting (4 agents)

## Workspace Configuration

```yaml
Workspace ID: 72e316b2-cc46-4d4b-93e1-3561ebae0b82
Tenant ID: dbf22f42-e951-4d07-8579-1400a6f9a473
Subscription ID: 4167334c-383c-4f4a-98fa-f4f591d709b3
Organization: PurpleX Lab
Environment: Production
```

## Directory Structure

```
hierarchy/
├── README.md                              # Hierarchy overview
├── config.yaml                            # Main configuration
├── agents/
│   ├── tier1-agents.yaml                 # 4 Tier 1 agents
│   ├── tier2-agents.yaml                 # 4 Tier 2 agents
│   ├── tier3-forensic-agents.yaml        # 4 Tier 3 agents
│   └── cloud-hunter-agents.yaml          # 4 Cloud Hunter agents
├── roles/
│   └── roles-matrix.yaml                 # Roles and responsibilities
├── skills/
│   └── skills-matrix.yaml                # Skills progression (4 levels)
├── schema/
│   ├── agent-schema.json                 # Agent definition schema
│   ├── alert-schema.json                 # Alert schema
│   ├── investigation-schema.json         # Investigation schema
│   └── case-schema.json                  # Forensic case schema
└── data/
    ├── data-sources.yaml                 # Data sources and integrations
    ├── workflows.yaml                    # Workflows and SLAs
    └── escalation-paths.yaml             # Escalation rules and procedures
```

## Agents Summary

### Tier 1 - Alert Triage & Routing (SLA: 1 hour)

| Agent ID             | Name          | Capability                 | SLA    |
| -------------------- | ------------- | -------------------------- | ------ |
| tier1-alert-parser   | AlertParser   | Parse & normalize alerts   | 5 min  |
| tier1-alert-enricher | AlertEnricher | Add context & threat intel | 2 min  |
| tier1-alert-router   | AlertRouter   | Route to destinations      | 1 min  |
| tier1-fp-eliminator  | FPEliminator  | Filter false positives     | 30 sec |

### Tier 2 - Investigation & Analysis (SLA: 4 hours)

| Agent ID                   | Name                | Specialty                     | SLA    |
| -------------------------- | ------------------- | ----------------------------- | ------ |
| tier2-malware-analyzer     | MalwareAnalyzer     | File & process analysis       | 30 min |
| tier2-network-investigator | NetworkInvestigator | Network anomaly investigation | 20 min |
| tier2-identity-analyzer    | IdentityAnalyzer    | Identity & access risk        | 15 min |
| tier2-threat-assessor      | ThreatAssessor      | Severity & impact assessment  | 25 min |

### Tier 3 - Forensic Analysis (SLA: 24 hours)

| Agent ID                     | Name                  | Specialty                | SLA     |
| ---------------------------- | --------------------- | ------------------------ | ------- |
| tier3-forensic-investigator  | ForensicInvestigator  | Deep forensic analysis   | 4 hours |
| tier3-incident-reconstructor | IncidentReconstructor | Timeline reconstruction  | 6 hours |
| tier3-evidence-collector     | EvidenceCollector     | Evidence preservation    | 2 hours |
| tier3-root-cause-analyzer    | RootCauseAnalyzer     | Root cause determination | 8 hours |

### Cloud Threat Hunter - Proactive Hunting

| Agent ID                             | Name                   | Focus                    | Frequency |
| ------------------------------------ | ---------------------- | ------------------------ | --------- |
| cloud-hunter-infrastructure-analyzer | InfrastructureAnalyzer | Cloud misconfigurations  | 2 hours   |
| cloud-hunter-log-anomaly-detector    | LogAnomalyDetector     | Cloud log analysis       | 30 min    |
| cloud-hunter-threat-intel-enricher   | ThreatIntelEnricher    | Threat intel correlation | 1 hour    |
| cloud-hunter-proactive-hunter        | ProactiveHunter        | Advanced threat hunting  | 4 hours   |

## Roles Matrix

**16 defined roles** across all tiers:

- 4 Tier 1 specialist roles
- 4 Tier 2 investigator roles
- 4 Tier 3 forensic expert roles
- 4 Cloud Threat Hunter analyst roles

Each role includes:

- Clear responsibilities
- Required skills
- Decision authority level
- Escalation authority

## Skills Framework

**40+ skills** organized in 5 categories:

### Core Skills (Level 1-2)

- Alert parsing & normalization
- Threat intelligence integration
- Alert classification
- Pattern recognition

### Investigation Skills (Level 3)

- Malware analysis
- Network analysis
- Identity risk assessment
- Risk assessment

### Forensic Skills (Level 4)

- Forensic analysis
- Windows internals
- Timeline analysis
- Evidence preservation
- Root cause analysis

### Cloud Skills (Level 3)

- Cloud security assessment
- Cloud log analysis
- Threat hunting

### Technical & Soft Skills

- Regex mastery, ML inference
- Query optimization, graph analysis
- Communication, documentation

## Schemas Defined

### 1. Agent Schema (agent-schema.json)

Defines agent configuration including:

- ID, name, tier, role
- Capabilities & data sources
- Skills & integration points
- SLA response times
- Success metrics

### 2. Alert Schema (alert-schema.json)

Unified alert format with:

- Alert properties (severity, status, title)
- Affected entities
- Evidence & enrichment data
- Investigation linkage
- MITRE ATT&CK mappings

### 3. Investigation Schema (investigation-schema.json)

Complete investigation tracking:

- Timeline reconstruction
- Findings documentation
- Root cause analysis
- Remediation actions
- Business impact assessment
- Escalation history

### 4. Case Schema (case-schema.json)

Forensic case management:

- Evidence collection & tracking
- Chain of custody
- Forensic findings
- Legal considerations
- Case reports
- Compliance documentation

## Data Sources

**8 primary data sources** configured:

- Microsoft Defender XDR
- Microsoft Entra ID
- Azure Security Center
- Microsoft Defender for Cloud Apps
- AWS CloudTrail
- GCP Cloud Audit Logs
- External threat intelligence feeds
- Internal data stores (alerts, investigations, evidence, baselines)

## Workflows Defined

### Standard Workflow: Alert to Resolution

10-step process from alert ingestion to closure:

1. Alert received
2. Normalization
3. Enrichment
4. False positive check
5. Routing decision
6. Tier 1 investigation (if applicable)
7. Tier 2 investigation (if escalated)
8. Tier 3 forensics (if confirmed incident)
9. Remediation
10. Closure

### Cloud Threat Hunting Workflow

Continuous proactive hunting:

1. Cloud data collection
2. Infrastructure analysis
3. Log anomaly detection
4. Threat intelligence enrichment
5. Proactive hunting
6. Finding aggregation
7. Report generation

### Escalation Workflows

- Alert to Investigation (Tier 1 → Tier 2)
- Investigation to Forensics (Tier 2 → Tier 3)
- Cloud Finding to Tier 2
- Case to Legal

## SLA Definitions

### Tier 1 Response Times

- Critical: 15 min response, 30 min escalation
- High: 1 hour response, 2 hour escalation
- Medium: 2 hour response, 4 hour escalation
- Low: 4 hour response, 24 hour escalation

### Tier 2 Response Times

- Critical: 1 hour start, 4 hour findings, 8 hour escalation
- High: 4 hour start, 24 hour findings, 24 hour escalation
- Medium: 8 hour start, 48 hour findings, 72 hour escalation

### Tier 3 Response Times

- Critical: 8 hour forensic start, 48 hour initial, 72 hour final
- High: 24 hour start, 72 hour initial, 120 hour final

## Escalation Paths

Comprehensive escalation matrix including:

### Alert Routing

- Critical severity → Tier 2 immediate + Tier 3 standby
- High severity → Tier 2 + Tier 3 if not resolved
- Medium severity → Tier 1 investigation, escalate if needed
- Low severity → Batch review queue

### Investigation Escalation

- Unconfirmed threat → Continue monitoring
- Suspicious activity → Escalate to Tier 2
- Confirmed incident → Escalate to Tier 3
- Active breach → Immediate crisis response

### Forensic Escalation

- Forensic case creation requirements
- Legal implications detection
- Criminal activity detection & law enforcement coordination

### Cloud Hunter Escalation

- Infrastructure misconfiguration → Remediation tracking (30 days)
- Security vulnerability → Tier 2 investigation (14 days)
- Active threat indicator → Immediate response

## Key Features

✅ **16 Agents** across 4 operational tiers
✅ **16 Defined Roles** with clear responsibilities
✅ **40+ Skills** with progression framework
✅ **4 JSON Schemas** for standardized data
✅ **8 Data Sources** integrated
✅ **5 Workflows** defined with steps
✅ **Comprehensive Escalation Matrix** with decision paths
✅ **SLA Definitions** for all tiers
✅ **Notification Templates** for escalations
✅ **Handoff Procedures** between tiers

## Getting Started

1. **Review Configuration**: Start with `config.yaml` for overall hierarchy settings
2. **Understand Agents**: Review agent definitions in the `agents/` directory
3. **Study Roles**: Check `roles-matrix.yaml` for role assignments
4. **Learn Skills**: Review `skills-matrix.yaml` for skill progression
5. **Understand Data**: Review `data-sources.yaml` and `workflows.yaml`
6. **Plan Escalations**: Study `escalation-paths.yaml` for decision trees

## Integration Points

- Microsoft Defender XDR
- Azure Security Center
- Microsoft Entra ID
- Defender for Cloud Apps
- AWS CloudTrail
- GCP Cloud Audit Logs
- Threat intelligence platforms (MISP, Anomali, etc.)
- IT ticketing/SOAR systems
- Legal/Compliance systems
- Communications platforms (Teams, Slack)

## Customization

All components can be customized:

- Adjust SLA times based on your organization's needs
- Add/remove agents or skills
- Modify escalation thresholds
- Update data sources based on your environment
- Customize notification recipients
- Extend schemas for additional fields

---

**Created**: February 14, 2026
**Workspace**: PurpleX Lab - Sentinel MCP
**Version**: 1.0.0
