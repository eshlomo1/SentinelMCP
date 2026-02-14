# Changelog

All notable changes to the SentinelMCP project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-02-14

### Added

**Core Framework**

- Complete 4-tier MDR operational hierarchy
- 16 specialized security agents across 4 tiers
- 16 roles with 1:1 mapping to agents
- 40+ skills organized in 4-level progression framework
- Role-based access control (RBAC) structure

**Agents (16 total)**

- **Tier 1 (Triage)**: AlertParser, AlertEnricher, AlertRouter, FPEliminator
- **Tier 2 (Investigation)**: MalwareAnalyzer, NetworkInvestigator, IdentityAnalyzer, ThreatAssessor
- **Tier 3 (Forensic)**: ForensicInvestigator, IncidentReconstructor, EvidenceCollector, RootCauseAnalyzer
- **Cloud Hunter**: InfrastructureAnalyzer, LogAnomalyDetector, ThreatIntelEnricher, ProactiveHunter

**Data Integration**

- 8 integrated data sources (Defender XDR, Entra ID, Azure Security, Azure Monitor, AWS CloudTrail, GCP Audit, SIEM, Threat Intel)
- 5 operational workflows with step definitions
- Unified alert normalization and enrichment
- Multi-source data correlation

**Schemas & Validation**

- 4 JSON schemas for validation (agents, alerts, investigations, cases)
- Data structure standardization
- Type validation for all major data objects

**Escalation & Response**

- 4 escalation matrices with decision trees
- SLA definitions by severity level
- Escalation paths and notification templates
- Authority and responsibility mapping

**Documentation**

- Comprehensive README with architecture overview
- Hierarchy summary with all components
- Architecture diagrams and visual flows
- Quick reference guide with checklists
- Navigation index and file guide
- Contributing guidelines
- MIT License

**Configuration**

- Workspace configuration (Sentinel workspace details)
- Data source definitions
- Workflow definitions
- Escalation path templates
- SLA configurations by tier and severity

**Development Setup**

- Git repository initialized
- GitHub remote configured (eshlomo1/SentinelMCP)
- .gitignore with standard exclusions
- Contributing guide for team collaboration
- Semantic versioning structure

### Key Features

- **Multi-Tier Architecture**: Triage → Investigation → Forensic path with parallel Cloud Hunter operations
- **Role-Based Operations**: Clear roles with defined responsibilities and escalation authority
- **Skill Progression**: 4-level skill framework (Analyst → Senior Analyst → Investigator → Expert)
- **Automated Workflows**: 5 predefined workflows for alert handling and incident response
- **Data Validation**: JSON schemas ensure data consistency across all tiers
- **Escalation Automation**: Decision-tree-based escalation with SLA tracking
- **Evidence Management**: Tier 3 focus on legal compliance and evidence chain of custody

### Technical Specifications

- **Total Files**: 23 (17 configuration/schema files + 6 documentation files)
- **Total Lines**: 4,987 lines
- **Configuration**: YAML-based for readability and version control
- **Schemas**: JSON for validation against strict data structures
- **Documentation**: Markdown with ASCII diagrams

### Workspace Integration

- **Sentinel Workspace**: 72e316b2-cc46-4d4b-93e1-3561ebae0b82
- **Tenant ID**: dbf22f42-e951-4d07-8579-1400a6f9a473
- **Subscription ID**: 4167334c-383c-4f4a-98fa-f4f591d709b3
- **Organization**: PurpleX Lab
- **Environment**: Production

### SLA Definitions

**Critical Alerts**

- Tier 1: 30 seconds response
- Tier 2: 5 minutes response

**High Priority Alerts**

- Tier 1: 2 minutes response
- Tier 2: 15 minutes response

**Medium Priority Alerts**

- Tier 1: 5 minutes response
- Tier 2: 30 minutes response

**Low Priority Alerts**

- Tier 1: 15 minutes response
- Tier 2: 4 hours response

### Files Included

```
SentinelMCP/
├── README.md                          # Project overview (production-ready)
├── CHANGELOG.md                       # Version history
├── CONTRIBUTING.md                    # Contribution guidelines
├── LICENSE                            # MIT License
├── .gitignore                         # Git ignore rules
│
└── hierarchy/                         # Main MDR framework
    ├── README.md                      # Hierarchy documentation
    ├── INDEX.md                       # Navigation guide
    ├── HIERARCHY_SUMMARY.md           # Complete reference
    ├── ARCHITECTURE_DIAGRAM.md        # Visual diagrams
    ├── QUICK_REFERENCE.md             # Quick lookup
    ├── config.yaml                    # Root configuration
    │
    ├── agents/                        # 16 Agent definitions
    │   ├── tier1-agents.yaml          # 4 Triage agents
    │   ├── tier2-agents.yaml          # 4 Investigation agents
    │   ├── tier3-forensic-agents.yaml # 4 Forensic agents
    │   └── cloud-hunter-agents.yaml   # 4 Cloud hunting agents
    │
    ├── roles/                         # Role definitions
    │   └── roles-matrix.yaml          # 16 roles with mappings
    │
    ├── skills/                        # Skills framework
    │   └── skills-matrix.yaml         # 40+ skills organized by level
    │
    ├── schema/                        # Validation schemas
    │   ├── agent-schema.json          # Agent validation
    │   ├── alert-schema.json          # Alert format validation
    │   ├── investigation-schema.json  # Investigation tracking
    │   └── case-schema.json           # Forensic case validation
    │
    └── data/                          # Configuration & workflows
        ├── config.yaml                # Workspace & tier configuration
        ├── data-sources.yaml          # 8 integrated data sources
        ├── workflows.yaml             # 5 operational workflows
        └── escalation-paths.yaml      # 4 escalation matrices
```

### Getting Started

1. Clone the repository: `git clone https://github.com/eshlomo1/SentinelMCP.git`
2. Review [README.md](README.md) for project overview
3. Read [hierarchy/README.md](hierarchy/README.md) for hierarchy details
4. Check [hierarchy/QUICK_REFERENCE.md](hierarchy/QUICK_REFERENCE.md) for quick answers
5. Review [hierarchy/INDEX.md](hierarchy/INDEX.md) for navigation
6. Explore agent definitions in `hierarchy/agents/`

### Next Steps

Future releases may include:

- [ ] Python SDK for agent implementation
- [ ] PowerShell runbooks for Azure Automation
- [ ] KQL (Kusto Query Language) detection rules
- [ ] Logic Apps templates for automation
- [ ] SOAR (Sentinel SOAR) playbooks
- [ ] Mobile app for operational overview
- [ ] Enhanced analytics and dashboards
- [ ] Integration with third-party tools
- [ ] Additional cloud provider support
- [ ] Advanced threat hunting templates

### Acknowledgments

Created by the PurpleX Lab security operations team for enterprise-grade threat detection and response.

---

**Release Date**: February 14, 2026  
**Commit Hash**: 485227a  
**Repository**: https://github.com/eshlomo1/SentinelMCP  
**License**: MIT
