# SentinelMCP - Microsoft Sentinel Managed Detection & Response

A comprehensive, production-ready Managed Detection and Response (MDR) framework for Microsoft Sentinel, featuring 4-tier operational hierarchy, 16 specialized agents, and automated threat hunting capabilities.

## Overview

**SentinelMCP** is an enterprise-grade MDR operations architecture designed for the **PurpleX Lab** organization. It provides a complete framework for managing security alerts, investigations, and threat hunting across Microsoft Sentinel with clear role definitions, skill progression models, and automated escalation workflows.

### Key Features

- **4-Tier Operational Hierarchy**
  - **Tier 1 (Triage)**: Alert normalization, enrichment, and false positive elimination
  - **Tier 2 (Investigation)**: In-depth malware, network, and identity analysis
  - **Tier 3 (Forensic)**: Root cause analysis and legal evidence handling
  - **Cloud Hunter**: Proactive threat hunting across cloud infrastructure

- **16 Specialized Agents** with defined roles, capabilities, and SLAs
- **40+ Skill Framework** with 4-level progression (Analyst → Senior Analyst → Investigator → Expert)
- **5 Operational Workflows** including alert-to-resolution flow
- **4 Escalation Matrices** with decision trees and notification templates
- **8 Integrated Data Sources** (Defender XDR, Entra ID, Azure, AWS, GCP, threat intelligence)
- **4 JSON Schemas** for data validation and standardization

## Repository Structure

```
SentinelMCP/
├── README.md                          # This file - Project overview
├── TIER_INTEGRATION.md                # Tier-to-tier escalation framework
├── HIERARCHY_README.md                # Hierarchy overview and organization
├── INDEX.md                           # Navigation index and quick links
├── HIERARCHY_SUMMARY.md               # Complete component summary
├── ARCHITECTURE_DIAGRAM.md            # Visual architecture diagrams
├── QUICK_REFERENCE.md                 # Quick reference and checklists
├── CHANGELOG.md                       # Version history
├── CONTRIBUTING.md                    # Contributor guidelines
├── LICENSE                            # MIT License
├── .gitignore                         # Git ignore rules
│
├── config.yaml                        # Main workspace configuration
│
├── agents/                            # Agent definitions (16 agents, 4 tiers)
│   ├── tier1-agents.yaml              # Triage agents (Alert normalization, enrichment, routing)
│   ├── tier2-agents.yaml              # Investigation agents (Malware, network, identity, threat assessment)
│   ├── tier3-forensic-agents.yaml     # Forensic agents (Investigation, reconstruction, evidence, root cause)
│   └── cloud-hunter-agents.yaml       # Cloud hunting agents (Infrastructure, logs, threat intel, proactive)
│
├── roles/                             # Role definitions (16 roles, 1:1 with agents)
│   └── roles-matrix.yaml              # Complete role matrix with responsibilities and authority
│
├── skills/                            # Skills framework
│   └── skills-matrix.yaml             # 40+ skills organized by level and category
│
├── schema/                            # Data validation schemas (JSON)
│   ├── agent-schema.json              # Agent configuration validation
│   ├── alert-schema.json              # Alert data validation
│   ├── investigation-schema.json      # Investigation tracking validation
│   └── case-schema.json               # Forensic case validation
│
└── data/                              # Data and configuration
    ├── config.yaml                    # Workspace settings, SLAs, escalation triggers
    ├── tier-integration.yaml          # Tier-to-tier escalation criteria and processes
    ├── data-sources.yaml              # 8 integrated data sources and patterns
    ├── workflows.yaml                 # 5 operational workflows with steps
    └── escalation-paths.yaml          # 4 escalation matrices with templates
```

## Quick Start

### 1. Understanding the Hierarchy

Start with these files in order:

```
→ HIERARCHY_README.md              (Overview, 5 min)
→ INDEX.md                         (Navigation guide, 3 min)
→ QUICK_REFERENCE.md               (Quick lookup, 2 min)
→ ARCHITECTURE_DIAGRAM.md          (Visual guide, 5 min)
→ HIERARCHY_SUMMARY.md             (Complete details, 15 min)
```

### 2. Key Components

#### Agents (16 total)

Each agent has:

- Unique ID and role_id linking to roles
- Defined capabilities and data sources
- 3-5 required skills from the skill matrix
- SLA response times by severity
- Success metrics for evaluation

Read: `agents/`

#### Roles (16 total)

Each role has:

- Primary agent responsibility
- Key responsibilities and decision authority
- Required skills and escalation authority
- Mapped to one agent (1:1 correspondence)

Read: `roles/roles-matrix.yaml`

#### Skills (40+)

Organized in 4 levels:

- **Level 1**: Analyst (entry-level)
- **Level 2**: Senior Analyst (intermediate)
- **Level 3**: Investigator (advanced)
- **Level 4**: Expert (specialized)

Read: `skills/skills-matrix.yaml`

#### Workflows (5 total)

- Alert → Investigation → Resolution
- Cloud hunting → Threat assessment
- Escalation procedures
- Evidence collection
- Incident documentation

Read: `data/workflows.yaml`

### 3. Configuration

#### Workspace Details

- **Workspace ID**: 72e316b2-cc46-4d4b-93e1-3561ebae0b82
- **Tenant ID**: dbf22f42-e951-4d07-8579-1400a6f9a473
- **Subscription ID**: 4167334c-383c-4f4a-98fa-f4f591d709b3
- **Organization**: PurpleX Lab
- **Environment**: Production

#### SLAs by Severity

- **Critical**: 30 seconds (Tier 1) → 5 minutes (Tier 2)
- **High**: 2 minutes (Tier 1) → 15 minutes (Tier 2)
- **Medium**: 5 minutes (Tier 1) → 30 minutes (Tier 2)
- **Low**: 15 minutes (Tier 1) → 4 hours (Tier 2)

Read: `data/config.yaml` or `config.yaml`

## Architecture Overview

```
┌─────────────────────────────────────────────────────────────────┐
│                      DATA SOURCES                                │
│  Defender XDR │ Entra ID │ Azure │ AWS │ GCP │ Threat Intel    │
└────────────────────────────────┬────────────────────────────────┘
                                 │
                                 ▼
        ┌────────────────────────────────────────────┐
        │      TIER 1: TRIAGE & NORMALIZATION        │
        │  • Alert Parser      • Alert Router         │
        │  • Alert Enricher    • FP Eliminator        │
        └────────────────────────────────────────────┘
              │                           │
              │                           ▼
              │        ┌──────────────────────────────┐
              │        │   CLOUD HUNTER (Parallel)    │
              │        │  • Infrastructure Analyzer   │
              │        │  • Log Anomaly Detector      │
              │        │  • Threat Intel Enricher     │
              │        │  • Proactive Hunter          │
              │        └──────────────────────────────┘
              │
              ▼
    ┌────────────────────────────────────────────┐
    │    TIER 2: INVESTIGATION & ANALYSIS        │
    │  • Malware Analyzer                        │
    │  • Network Investigator  • Identity Analyzer│
    │  • Threat Assessor                         │
    └──────────────────┬───────────────────────┘
                       │
                       ▼
    ┌────────────────────────────────────────────┐
    │   TIER 3: FORENSIC & ROOT CAUSE ANALYSIS  │
    │  • Forensic Investigator                   │
    │  • Incident Reconstructor                  │
    │  • Evidence Collector                      │
    │  • Root Cause Analyzer                     │
    └────────────────────────────────────────────┘
                       │
                       ▼
          ┌────────────────────────┐
          │   RESOLUTION OUTPUT    │
          │  • Investigation Case  │
          │  • Evidence Package    │
          │  • Root Cause Report   │
          │  • Remediation Plan    │
          └────────────────────────┘
```

## Data Integration

### 8 Integrated Data Sources

1. **Microsoft Defender XDR** - Endpoint, email, cloud app threats
2. **Entra ID** - User authentication and directory events
3. **Azure Security Center** - Infrastructure alerts and vulnerability data
4. **Azure Monitor** - Application logs and diagnostics
5. **AWS CloudTrail** - Cloud infrastructure events
6. **GCP Audit Logs** - Google Cloud activity
7. **Third-Party SIEM** - Additional security tools integration
8. **Threat Intelligence Feeds** - External threat context

### Data Flow Patterns

- **Alert Ingestion**: Raw alerts → Tier 1 normalization → unified format
- **Investigation Flow**: Alert enrichment → Tier 2 analysis → escalation decision
- **Forensic Deep-Dive**: Confirmed incident → Tier 3 evidence collection → root cause
- **Proactive Hunting**: Cloud Hunter parallel queries → anomaly detection → threat assessment
- **Escalation**: Decision trees based on severity and investigation findings

## Validation & Schemas

All data is validated against JSON schemas:

- **agent-schema.json** - Validates agent definitions
- **alert-schema.json** - Validates alert structure and fields
- **investigation-schema.json** - Validates investigation tracking
- **case-schema.json** - Validates forensic case documentation

## Getting Started

### Prerequisites

- Microsoft Sentinel workspace
- Access to data sources (Defender, Entra ID, Azure, etc.)
- Python 3.8+ or PowerShell 7+ (for implementing agents)
- Git for version control

### Installation

```bash
# Clone the repository
git clone https://github.com/eshlomo1/SentinelMCP.git
cd SentinelMCP

# Review the hierarchy
cat HIERARCHY_README.md

# Start with quick reference
cat QUICK_REFERENCE.md

# Explore agents, roles, and skills
cat agents/tier1-agents.yaml
cat roles/roles-matrix.yaml
cat skills/skills-matrix.yaml
```

### Configuration

1. Update `data/config.yaml` with your workspace details
2. Configure data sources in `data/data-sources.yaml`
3. Adjust SLAs based on your organization's requirements
4. Customize workflows in `data/workflows.yaml`

### Implementation

The YAML definitions can be implemented as:

- **PowerShell Runbooks** - For Azure Automation
- **Python Scripts** - For Sentinel Analytics Rules
- **Logic Apps** - For workflow automation
- **Kusto Query Language (KQL)** - For detection rules
- **Playbook Templates** - For incident response

## File Statistics

```
Total Files:       17
Total Directories: 6
Total Lines:       4,029
Documentation:     2,000+ lines
Agents:            16 (4 files)
Roles:             16 (1 file)
Skills:            40+ (1 file)
Schemas:           4 JSON files
Workflows:         5 (1 file)
Escalation Paths:  4 matrices (1 file)
Data Sources:      8 (1 file)
```

## Agent Summary

### Tier 1: Triage (SLA: 5 min)

- **AlertParser** (role_id: t1-alert-normalization)
- **AlertEnricher** (role_id: t1-alert-enrichment)
- **AlertRouter** (role_id: t1-alert-routing)
- **FPEliminator** (role_id: t1-fp-detection)

### Tier 2: Investigation (SLA: 30 min)

- **MalwareAnalyzer** (role_id: t2-malware-analysis)
- **NetworkInvestigator** (role_id: t2-network-investigation)
- **IdentityAnalyzer** (role_id: t2-identity-analysis)
- **ThreatAssessor** (role_id: t2-threat-assessment)

### Tier 3: Forensic (SLA: 8 hours)

- **ForensicInvestigator** (role_id: t3-forensic-investigation)
- **IncidentReconstructor** (role_id: t3-incident-reconstruction)
- **EvidenceCollector** (role_id: t3-evidence-collection)
- **RootCauseAnalyzer** (role_id: t3-root-cause-analysis)

### Cloud Hunter: Proactive (SLA: 4 hours)

- **InfrastructureAnalyzer** (role_id: ch-infrastructure-security)
- **LogAnomalyDetector** (role_id: ch-log-analysis)
- **ThreatIntelEnricher** (role_id: ch-threat-intelligence)
- **ProactiveHunter** (role_id: ch-proactive-hunting)

## Documentation Files

| Document                                             | Purpose                                                  | Read Time |
| ---------------------------------------------------- | -------------------------------------------------------- | --------- |
| [TIER_INTEGRATION.md](TIER_INTEGRATION.md)           | Tier-to-tier escalation framework and decision criteria  | 10 min    |
| [HIERARCHY_SUMMARY.md](HIERARCHY_SUMMARY.md)         | Complete overview of all components                      | 15 min    |
| [INDEX.md](INDEX.md)                                 | Navigation guide and quick links                         | 5 min     |
| [QUICK_REFERENCE.md](QUICK_REFERENCE.md)             | Quick lookup and checklists                              | 3 min     |
| [ARCHITECTURE_DIAGRAM.md](ARCHITECTURE_DIAGRAM.md)   | Visual architecture and flows                            | 5 min     |
| [HIERARCHY_README.md](HIERARCHY_README.md)           | Hierarchy-specific documentation                         | 5 min     |

## Best Practices

### Alert Handling

- Route alerts to appropriate tier based on severity
- Enrich with context before escalation
- Track investigation progress and timeline
- Document decisions and findings

### Investigation

- Use consistent data collection methods
- Maintain chain of custody for evidence
- Document all findings and conclusions
- Escalate when scope grows beyond tier capability

### Forensic Analysis

- Collect all relevant evidence
- Preserve integrity of evidence
- Follow legal requirements
- Provide detailed root cause analysis

### Cloud Hunting

- Run continuous anomaly detection
- Correlate findings across accounts
- Enrich with threat intelligence
- Feed findings to investigation tier

## Support & Contribution

### Using This Framework

1. Read the [HIERARCHY_README.md](HIERARCHY_README.md) for overview
2. Review agent capabilities in `agents/`
3. Check role responsibilities in `roles/roles-matrix.yaml`
4. Customize workflows in `data/workflows.yaml`
5. Implement agents for your environment

### Customization

- Adjust agent capabilities for your use case
- Modify SLAs based on organizational requirements
- Add new data sources in `data-sources.yaml`
- Create additional workflows as needed
- Extend skills matrix for your team

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Organization

**SentinelMCP** is maintained by the **PurpleX Lab** security operations team.

- **Workspace**: Microsoft Sentinel
- **Tenant**: Azure Active Directory
- **Environment**: Production

## Version History

- **v1.0.0** (Feb 2026) - Initial release with 16 agents, 16 roles, 40+ skills

## Contact & Support

For questions or issues:

1. Review the [INDEX.md](INDEX.md) for navigation
2. Check [QUICK_REFERENCE.md](QUICK_REFERENCE.md) for quick answers
3. Consult the specific agent files in `agents/`
4. Review workflow definitions in `data/workflows.yaml`

---

**Last Updated**: February 14, 2026

**Repository**: [https://github.com/eshlomo1/SentinelMCP](https://github.com/eshlomo1/SentinelMCP)
