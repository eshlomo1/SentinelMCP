# Quick Reference Guide

## Complete Hierarchy Structure Created

**Total Files**: 17
**Total Directories**: 6

### Directory Breakdown

```
hierarchy/                          (6 subdirectories)
├── agents/                         (4 agent definition files)
├── roles/                          (1 roles matrix)
├── skills/                         (1 skills matrix)
├── schema/                         (4 schema files)
├── data/                           (3 data flow files)
└── root level                      (4 documentation files)
```

## Content Summary

### Agents (16 Total)

- **Tier 1** (4): AlertParser, AlertEnricher, AlertRouter, FPEliminator
- **Tier 2** (4): MalwareAnalyzer, NetworkInvestigator, IdentityAnalyzer, ThreatAssessor
- **Tier 3** (4): ForensicInvestigator, IncidentReconstructor, EvidenceCollector, RootCauseAnalyzer
- **Cloud Hunter** (4): InfrastructureAnalyzer, LogAnomalyDetector, ThreatIntelEnricher, ProactiveHunter

### Roles (16 Total)

- **Tier 1** (4): Alert Normalization, Enrichment, Routing, FP Detection
- **Tier 2** (4): Malware Analysis, Network Analysis, Identity Analysis, Threat Assessment
- **Tier 3** (4): Forensic Investigation, Reconstruction, Evidence, Root Cause
- **Cloud Hunter** (4): Infrastructure, Log Analysis, Threat Intel, Proactive Hunting

### Skills (40+)

- **Level 1-2**: Core skills (alert parsing, enrichment, classification)
- **Level 3**: Investigation skills (malware, network, identity analysis)
- **Level 4**: Forensic expert skills (forensics, windows, timeline, evidence)
- **Cloud**: Cloud-specific skills
- **Technical & Soft**: Query optimization, communication, documentation

### Schemas (4 Total)

- **agent-schema.json**: Agent configuration structure
- **alert-schema.json**: Unified alert format
- **investigation-schema.json**: Investigation tracking
- **case-schema.json**: Forensic case management

### Workflows (5 Total)

1. Standard Alert to Resolution (10-step process)
2. Cloud Threat Hunting (7-step continuous)
3. Alert to Investigation Escalation (Tier 1 → Tier 2)
4. Investigation to Forensics (Tier 2 → Tier 3)
5. Cloud Finding to Tier 2 (Cloud Hunter escalation)

### Data Sources (8 Total)

- Microsoft Defender XDR
- Microsoft Entra ID
- Azure Security Center
- Microsoft Defender for Cloud Apps
- AWS CloudTrail
- GCP Cloud Audit Logs
- External Threat Intelligence Feeds
- Internal Data Stores

## Key Features

- [COMPLETE] **Complete MDR Hierarchy**: All 4 tiers fully defined
- [COMPLETE] **SLA Definitions**: Response times for all severity levels
- [COMPLETE] **Escalation Paths**: Clear decision matrices for escalations
- [COMPLETE] **Role-based Access**: 16 defined roles with responsibilities
- [COMPLETE] **Skill Progression**: 4-level skill framework
- [COMPLETE] **Data Integration**: 8 integrated data sources
- [COMPLETE] **Workflow Documentation**: 5 complete workflows with steps
- [COMPLETE] **JSON Schemas**: 4 standardized data schemas
- [COMPLETE] **Notification Templates**: 3 escalation notification templates
- [COMPLETE] **Chain of Custody**: Forensic evidence tracking

## File Quick Reference

### Documentation Files

| File                    | Purpose            | Read Time |
| ----------------------- | ------------------ | --------- |
| README.md               | Hierarchy overview | 5 min     |
| HIERARCHY_SUMMARY.md    | Complete summary   | 10 min    |
| ARCHITECTURE_DIAGRAM.md | Visual diagrams    | 5 min     |
| QUICK_REFERENCE.md      | This file          | 3 min     |

### Configuration Files

| File               | Content               | Size   |
| ------------------ | --------------------- | ------ |
| config.yaml        | Main hierarchy config | 1.2 KB |
| roles-matrix.yaml  | 16 role definitions   | 8.5 KB |
| skills-matrix.yaml | 40+ skill definitions | 7.8 KB |

### Agent Definitions

| File                       | Agents | Details                                       |
| -------------------------- | ------ | --------------------------------------------- |
| tier1-agents.yaml          | 4      | Parse, Enrich, Route, FP Filter               |
| tier2-agents.yaml          | 4      | Malware, Network, Identity, Threat Assessment |
| tier3-forensic-agents.yaml | 4      | Forensics, Reconstruction, Evidence, RCA      |
| cloud-hunter-agents.yaml   | 4      | Infrastructure, Logs, TI, Proactive Hunt      |

### Schemas

| File                      | Purpose                | Records                 |
| ------------------------- | ---------------------- | ----------------------- |
| agent-schema.json         | Agent structure        | Single agent definition |
| alert-schema.json         | Alert format           | Single alert            |
| investigation-schema.json | Investigation tracking | Single investigation    |
| case-schema.json          | Forensic case          | Single case             |

### Data Flows

| File                  | Content                 | Sections               |
| --------------------- | ----------------------- | ---------------------- |
| data-sources.yaml     | 8 sources + 5 patterns  | External + Internal    |
| workflows.yaml        | 2 workflows + SLAs      | Step-by-step processes |
| escalation-paths.yaml | 4 matrices + procedures | Decision paths         |

## Getting Started Steps

1. **Start Here**: Read [README.md](README.md)
2. **Understand Structure**: Review [HIERARCHY_SUMMARY.md](HIERARCHY_SUMMARY.md)
3. **View Architecture**: Check [ARCHITECTURE_DIAGRAM.md](ARCHITECTURE_DIAGRAM.md)
4. **Review Configuration**: Study [config.yaml](config.yaml)
5. **Explore Agents**: Read agent files in [agents/](agents/)
6. **Understand Roles**: Review [roles/roles-matrix.yaml](roles/roles-matrix.yaml)
7. **Learn Skills**: Study [skills/skills-matrix.yaml](skills/skills-matrix.yaml)
8. **Understand Data**: Review [data/data-sources.yaml](data/data-sources.yaml)
9. **Study Workflows**: Read [data/workflows.yaml](data/workflows.yaml)
10. **Master Escalations**: Study [data/escalation-paths.yaml](data/escalation-paths.yaml)

## Customization Points

### Easy to Customize

- SLA response times (adjust in config.yaml)
- Notification recipients (update in escalation-paths.yaml)
- Data sources (add/remove in data-sources.yaml)
- Skill requirements (modify skills-matrix.yaml)

### Moderate Customization

- Agent capabilities (update agent definitions)
- Workflow steps (revise in workflows.yaml)
- Escalation conditions (adjust decision matrices)

### Deep Customization

- Add new agents (requires schema updates)
- Add new tiers (comprehensive changes needed)
- Change hierarchical structure (affects all layers)

## Support Resources

### Workspace Configuration

- **Workspace ID**: 72e316b2-cc46-4d4b-93e1-3561ebae0b82
- **Tenant ID**: dbf22f42-e951-4d07-8579-1400a6f9a473
- **Subscription ID**: 4167334c-383c-4f4a-98fa-f4f591d709b3
- **Organization**: PurpleX Lab
- **Environment**: Production

### Key Metrics

- **Total Agents**: 16
- **Total Roles**: 16
- **Total Skills**: 40+
- **Skill Levels**: 4
- **Workflows**: 5
- **Data Sources**: 8
- **Escalation Matrices**: 4
- **Schemas**: 4

## Integration Checklist

- [ ] Review all agent definitions
- [ ] Confirm role assignments in your organization
- [ ] Validate SLA targets with leadership
- [ ] Configure data source connections
- [ ] Set up notification channels
- [ ] Train teams on escalation procedures
- [ ] Establish evidence management process
- [ ] Configure legal hold procedures
- [ ] Test end-to-end workflows
- [ ] Document customizations

## Quick Links

| Resource     | Location                                                 |
| ------------ | -------------------------------------------------------- |
| All Agents   | [agents/](agents/)                                       |
| Roles        | [roles/roles-matrix.yaml](roles/roles-matrix.yaml)       |
| Skills       | [skills/skills-matrix.yaml](skills/skills-matrix.yaml)   |
| Schemas      | [schema/](schema/)                                       |
| Data Sources | [data/data-sources.yaml](data/data-sources.yaml)         |
| Workflows    | [data/workflows.yaml](data/workflows.yaml)               |
| Escalations  | [data/escalation-paths.yaml](data/escalation-paths.yaml) |

## Statistics

```
AGENTS:        16 total
├─ Tier 1:     4 agents
├─ Tier 2:     4 agents
├─ Tier 3:     4 agents
└─ Cloud:      4 agents

ROLES:         16 total (1:1 with agents)
SKILLS:        40+ with 4 progression levels
WORKFLOWS:     5 complete processes
SLA TARGETS:   9 (3 per tier)
ESCALATIONS:   4 matrices
DATA SOURCES:  8 integrated
SCHEMAS:       4 standardized
TEMPLATES:     3 notification templates
```

---

**Version**: 1.0.0
**Created**: February 14, 2026
**Workspace**: PurpleX Lab - Sentinel MCP
