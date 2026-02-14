# SentinelMCP

**Enterprise-Grade Managed Detection & Response (MDR) Framework for Microsoft Sentinel**

A comprehensive, production-ready MDR operations architecture featuring a 4-tier operational hierarchy, 16 specialized agents, 40+ skills framework, and automated escalation workflows for the **PurpleX Lab** organization.

---

## 🚀 Quick Start

**New to SentinelMCP?** Start here:

1. **[START HERE: Overview](#overview)** (2 min) - What is SentinelMCP?
2. **[Setup Instructions](#setup)** (5 min) - Get started
3. **[Key Concepts](#key-concepts)** (5 min) - Core architecture

**Need more detail?** See [Documentation Guide](#documentation-guide) below.

---

## Overview

SentinelMCP is a complete MDR framework that transforms raw security alerts into actionable intelligence through a **4-tier investigation hierarchy**:

```
Tier 1: TRIAGE          → Alert normalization, enrichment, false positive elimination
  ↓
Tier 2: INVESTIGATION   → In-depth analysis (malware, network, identity)
  ↓
Tier 3: FORENSIC        → Root cause analysis, evidence collection
  ↓
Cloud Hunter (Parallel) → Proactive threat hunting across infrastructure
```

### Key Stats

- **16 Agents** with defined roles and responsibilities
- **16 Roles** with specific authorities and escalation paths
- **40+ Skills** organized in 4-level progression (Analyst → Senior Analyst → Investigator → Expert)
- **5 Workflows** for alert handling, investigation, and escalation
- **8 Data Sources** integrated (Defender XDR, Entra ID, Azure, AWS, GCP, etc.)
- **4 JSON Schemas** for data validation and standardization
- **Tier Integration** with automatic and manual escalation criteria

### What Problems Does It Solve?

✅ **Alert Fatigue** - Automatic false positive elimination  
✅ **Investigation Confusion** - Clear escalation paths and decision criteria  
✅ **Poor SLAs** - Automatic escalation when deadlines approach  
✅ **Evidence Loss** - Structured forensic case management  
✅ **Knowledge Gaps** - Skills progression and role definitions  
✅ **Inconsistent Process** - Standardized workflows at each tier

---

## Setup

### Prerequisites

- Microsoft Sentinel workspace (production or dev/test)
- Access to data sources (Defender XDR, Entra ID, Azure)
- Git (for version control)
- Python 3.8+ or PowerShell 7+ (for implementation)

### Installation

```bash
# Clone the repository
git clone https://github.com/eshlomo1/SentinelMCP.git
cd SentinelMCP

# Review configuration
cat config.yaml

# Check your workspace ID
grep "workspace_id" config.yaml
```

### Configuration

1. **Update workspace details** in `config.yaml`:

   ```yaml
   workspace_id: <your-workspace-id>
   tenant_id: <your-tenant-id>
   organization: <your-organization>
   ```

2. **Review SLAs** (`config.yaml`):

   ```yaml
   slas:
     critical: 5 minutes # Tier 1 response time
     high: 15 minutes
     medium: 1 hour
     low: 4 hours
   ```

3. **Customize agents** in `agents/`:
   - Modify SLAs based on your capacity
   - Add data sources specific to your environment
   - Adjust escalation criteria

---

## Key Concepts

### Tier Architecture

Each tier has **specific responsibilities** and **clear escalation criteria**:

| Tier             | Focus         | SLA       | Agents   | Output                                   |
| ---------------- | ------------- | --------- | -------- | ---------------------------------------- |
| **Tier 1**       | Triage        | 5-15 min  | 4 agents | Normalized alert, FP decision            |
| **Tier 2**       | Investigation | 30-60 min | 4 agents | Incident assessment, escalation decision |
| **Tier 3**       | Forensic      | 8 hours   | 4 agents | Root cause, evidence package             |
| **Cloud Hunter** | Proactive     | 4 hours   | 4 agents | Threat intel, anomalies                  |

### Escalation Framework

**Automatic escalation** happens when specific conditions are met:

- **Tier 1→2**: CRITICAL severity, confirmed compromise, lateral movement, data exfil attempts
- **Tier 2→3**: Multi-system compromise, APT indicators, legal/forensic requirements
- **Tier 3→Closure**: Root cause documented, evidence collected, case complete

See [DOCS/OPERATIONS/TIER_INTEGRATION.md](DOCS/OPERATIONS/TIER_INTEGRATION.md) for detailed escalation criteria.

### Roles & Responsibilities

Each agent has a corresponding **Role** that defines:

- Decision-making authority
- Escalation rights
- Required skills
- Success metrics

See [roles/roles-matrix.yaml](roles/roles-matrix.yaml) for complete role definitions.

---

## Documentation Guide

📚 **[START WITH DOCS/ →](DOCS/)**

SentinelMCP includes comprehensive documentation organized by role and use case:

- **For Operations Teams**: [DOCS/OPERATIONS/](DOCS/OPERATIONS/) - Procedures for Tiers 1, 2, and 3
- **For Architects**: [DOCS/ARCHITECTURE/](DOCS/ARCHITECTURE/) - System design and capacity planning
- **For Developers**: [DOCS/DEVELOPMENT/](DOCS/DEVELOPMENT/) - Building agents and integrating systems
- **For Everyone**: [DOCS/REFERENCE/](DOCS/REFERENCE/) - Quick reference and FAQs
- **For Troubleshooting**: [DOCS/SUPPORT/](DOCS/SUPPORT/) - Help and issue resolution

### 🚀 Quick Start

| Role                    | Start Here                                                                               | Time   |
| ----------------------- | ---------------------------------------------------------------------------------------- | ------ |
| **Tier 1 Analyst**      | [DOCS/OPERATIONS/TIER1_OPERATIONS.md](DOCS/OPERATIONS/TIER1_OPERATIONS.md)               | 10 min |
| **Tier 2 Investigator** | [DOCS/OPERATIONS/INVESTIGATION_WORKFLOW.md](DOCS/OPERATIONS/INVESTIGATION_WORKFLOW.md)   | 10 min |
| **Tier 3 Forensic**     | [DOCS/OPERATIONS/FORENSIC_PROCEDURES.md](DOCS/OPERATIONS/FORENSIC_PROCEDURES.md)         | 10 min |
| **Quick Answer**        | [DOCS/REFERENCE/QUICK_REFERENCE.md](DOCS/REFERENCE/QUICK_REFERENCE.md)                   | 2 min  |
| **Architect**           | [DOCS/ARCHITECTURE/ARCHITECTURE_OVERVIEW.md](DOCS/ARCHITECTURE/ARCHITECTURE_OVERVIEW.md) | 15 min |
| **Developer**           | [DOCS/DEVELOPMENT/README.md](DOCS/DEVELOPMENT/README.md)                                 | 10 min |

**Need help?** → [DOCS/README.md](DOCS/README.md) for complete documentation map

---

## Repository Structure

## Repository Structure

```
SentinelMCP/
├── README.md                      ← Main entry point (this file)
├── DOCS/                          ← Comprehensive documentation
│   ├── README.md                  ← Documentation navigation
│   ├── OPERATIONS/                ← Day-to-day operations procedures
│   │   ├── TIER_INTEGRATION.md    ← Escalation framework
│   │   ├── TIER1_OPERATIONS.md
│   │   ├── INVESTIGATION_WORKFLOW.md
│   │   ├── FORENSIC_PROCEDURES.md
│   │   ├── DATA_SOURCES.md
│   │   ├── CASE_MANAGEMENT.md
│   │   └── ESCALATION_CHECKLIST.md
│   ├── ARCHITECTURE/              ← System design
│   │   ├── ARCHITECTURE_OVERVIEW.md
│   │   ├── HIERARCHY.md
│   │   ├── DATA_FLOW.md
│   │   └── CAPACITY_PLANNING.md
│   ├── DEVELOPMENT/               ← Implementation guides
│   │   ├── AGENT_DEVELOPMENT.md
│   │   ├── INTEGRATION_GUIDE.md
│   │   ├── WORKFLOW_CUSTOM.md
│   │   └── SCHEMA_GUIDE.md
│   ├── REFERENCE/                 ← Quick lookups
│   │   ├── QUICK_REFERENCE.md
│   │   ├── ESCALATION_CRITERIA.md
│   │   ├── GLOSSARY.md
│   │   └── FAQ.md
│   └── SUPPORT/                   ← Help & troubleshooting
│       ├── TROUBLESHOOTING.md
│       ├── KNOWN_ISSUES.md
│       ├── PERFORMANCE_TUNING.md
│       └── VERSION_COMPATIBILITY.md
├── agents/                        ← 16 Agent definitions
│   ├── tier1-agents.yaml
│   ├── tier2-agents.yaml
│   ├── tier3-forensic-agents.yaml
│   └── cloud-hunter-agents.yaml
├── roles/                         ← 16 Role definitions
│   └── roles-matrix.yaml
├── skills/                        ← 40+ Skills framework
│   └── skills-matrix.yaml
├── schema/                        ← JSON validation schemas
│   ├── agent-schema.json
│   ├── alert-schema.json
│   ├── investigation-schema.json
│   └── case-schema.json
├── data/                          ← Configuration data
│   ├── config.yaml                ← Workspace configuration
│   ├── tier-integration.yaml      ← Escalation framework (technical)
│   ├── data-sources.yaml          ← Integrated data sources
│   ├── workflows.yaml             ← Operational workflows
│   └── escalation-paths.yaml      ← Escalation matrices
├── CHANGELOG.md                   ← Version history
├── CONTRIBUTING.md                ← Contributing guidelines
├── LICENSE                        ← MIT License
└── .gitignore
```

## Quick Start

### 1. Clone & Configure

```bash
git clone https://github.com/eshlomo1/SentinelMCP.git
cd SentinelMCP
cp config.yaml config.yaml.backup
# Edit config.yaml with your workspace details
```

### 2. Read the Docs

👉 **Start here**: [DOCS/README.md](DOCS/README.md)

This comprehensive guide covers:

- Role-specific documentation
- Task-based navigation
- Quick reference materials
- Troubleshooting guides

### 3. Choose Your Role

| Role                        | Start Here                                                                               |
| --------------------------- | ---------------------------------------------------------------------------------------- |
| **Tier 1 Alert Analyst**    | [DOCS/OPERATIONS/TIER1_OPERATIONS.md](DOCS/OPERATIONS/TIER1_OPERATIONS.md)               |
| **Tier 2 Investigator**     | [DOCS/OPERATIONS/INVESTIGATION_WORKFLOW.md](DOCS/OPERATIONS/INVESTIGATION_WORKFLOW.md)   |
| **Tier 3 Forensic Analyst** | [DOCS/OPERATIONS/FORENSIC_PROCEDURES.md](DOCS/OPERATIONS/FORENSIC_PROCEDURES.md)         |
| **Architect/Manager**       | [DOCS/ARCHITECTURE/ARCHITECTURE_OVERVIEW.md](DOCS/ARCHITECTURE/ARCHITECTURE_OVERVIEW.md) |
| **Developer/Engineer**      | [DOCS/DEVELOPMENT/README.md](DOCS/DEVELOPMENT/README.md)                                 |
| **Need Quick Answer?**      | [DOCS/REFERENCE/QUICK_REFERENCE.md](DOCS/REFERENCE/QUICK_REFERENCE.md)                   |

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

| Document                                           | Purpose                                                 | Read Time |
| -------------------------------------------------- | ------------------------------------------------------- | --------- |
| [TIER_INTEGRATION.md](TIER_INTEGRATION.md)         | Tier-to-tier escalation framework and decision criteria | 10 min    |
| [HIERARCHY_SUMMARY.md](HIERARCHY_SUMMARY.md)       | Complete overview of all components                     | 15 min    |
| [INDEX.md](INDEX.md)                               | Navigation guide and quick links                        | 5 min     |
| [QUICK_REFERENCE.md](QUICK_REFERENCE.md)           | Quick lookup and checklists                             | 3 min     |
| [ARCHITECTURE_DIAGRAM.md](ARCHITECTURE_DIAGRAM.md) | Visual architecture and flows                           | 5 min     |
| [HIERARCHY_README.md](HIERARCHY_README.md)         | Hierarchy-specific documentation                        | 5 min     |

## Support & Contribution

For detailed contribution guidelines and framework usage, see [CONTRIBUTING.md](CONTRIBUTING.md).

For best practices by operational area, see [DOCS/OPERATIONS/BEST_PRACTICES.md](DOCS/OPERATIONS/BEST_PRACTICES.md).

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
