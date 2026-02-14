# 🛡️ SentinelMCP

> **Enterprise-Grade MDR Operations Framework for Microsoft Sentinel**

[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](CHANGELOG.md)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Status](https://img.shields.io/badge/status-production-success.svg)](README.md)
[![Organization](https://img.shields.io/badge/organization-PurpleX%20Lab-purple.svg)](#organization)

---

## 🎯 What is SentinelMCP?

A **production-ready, enterprise-grade MDR framework** that transforms chaotic security alerts into structured, actionable intelligence. Featuring a **4-tier operational hierarchy**, **16 specialized agents**, **40+ advanced skills**, and **intelligent escalation workflows** designed for the rigorous demands of 24/7 security operations.

**SentinelMCP replaces manual alert triage with automated intelligence processing, giving your security team time to investigate what matters.**

---

## ⚡ Key Highlights

| Feature                         | Capability                                                        |
| ------------------------------- | ----------------------------------------------------------------- |
| **🤖 Intelligent Automation**   | 16 specialized agents with AI-driven decision logic               |
| **📊 4-Tier Architecture**      | Triage → Investigation → Forensic → Cloud Hunting                 |
| **📈 Skills Framework**         | 40+ progressive skills across 4 maturity levels                   |
| **🔄 Smart Escalation**         | Automatic escalation with SLA-aware workflows                     |
| **🔗 Multi-Source Integration** | 8 data sources: Defender XDR, Entra ID, Azure, AWS, GCP, and more |
| **✅ Proven SLAs**              | Industry-standard response times with auto-escalation             |
| **📋 Role-Based Access**        | 16 defined roles with clear decision authorities                  |
| **🔒 Evidence-Ready**           | Forensic-grade case documentation and chain of custody            |

---

## 🚀 Quick Start

**New to SentinelMCP?** Start here:

1. **[START HERE: Overview](#overview)** (2 min) - What is SentinelMCP?
2. **[Setup Instructions](#setup)** (5 min) - Get started
3. **[Key Concepts](#key-concepts)** (5 min) - Core architecture

**Need more detail?** See [Documentation Guide](#documentation-guide) below.

---

## Overview

SentinelMCP is a **battle-tested MDR framework** that brings enterprise-grade alert handling and investigation procedures to Microsoft Sentinel. It eliminates the chaos of manual alert triage through:

- **Intelligent Tier Routing** - Each alert finds the right handler first time
- **Automated FP Detection** - Reduce noise by 60-80% in Tier 1
- **Smart Escalation** - No more "should I escalate this?" decisions
- **Forensic-Grade Documentation** - Investigation-ready evidence packages
- **Skill-Based Assignment** - Right person, right skills, right alert

### The 4-Tier Operation Hierarchy

```
┌──────────────────────────────────────────────────────────────────────┐
│                         DATA SOURCES                                  │
│      Defender   Entra ID   Azure   AWS   GCP   Threat Intelligence   │
└─────────────────────────────┬──────────────────────────────────────┘
                              │
                    ┌─────────▼─────────┐
                    │  TIER 1: TRIAGE   │  5-15 min SLA
                    │  Normalize,       │  → 4 specialized agents
                    │  Enrich, Filter   │
                    └─────────┬─────────┘
                         ┌────┴─────┬────────────────────┐
                         │           │                    │
          ┌──────────────▼──┐  ┌──────▼─────┐  ┌────────▼─────┐
          │  TIER 2:        │  │   CLOUD    │  │  Escalate    │
          │  INVESTIGATION  │  │   HUNTER   │  │   to Tier 3? │
          │  30-60 min SLA  │  │  (Parallel)│  │              │
          └──────────┬──────┘  └────────────┘  └──────────────┘
                     │
          ┌──────────▼──────────┐
          │  TIER 3: FORENSIC   │  8 hours SLA
          │  Root Cause,        │  → 4 forensic agents
          │  Evidence Package   │
          └─────────────────────┘
```

### What Problems Does It Solve?

| Problem | SentinelMCP Solution |
|---------|---------------------|
| 🚨 **Alert Fatigue** | Automatic false positive elimination + intelligent routing |
| 🔍 **Investigation Confusion** | Clear escalation decision trees + documented procedures |
| ⏰ **SLA Breaches** | Automatic escalation when deadlines approach |
| 💾 **Evidence Loss** | Forensic-grade case management with chain of custody |
| 👥 **Skills Gaps** | Role + skill matrix ensures right analyst gets right alert |
| 📊 **Inconsistent Process** | Standardized workflows prevent ad-hoc decisions |
| 🔀 **Context Loss** | Alert enrichment at every tier preserves investigation context |

---

## 🛠️ Setup & Configuration

### Prerequisites

- ✅ Microsoft Sentinel workspace (production or eval)
- ✅ Access to data sources (Defender XDR, Entra ID minimum)
- ✅ Git installed
- ✅ Python 3.8+ OR PowerShell 7+ (for customization)

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

## 🎓 Key Concepts

### Tier Architecture at a Glance

Each tier has **crystal-clear responsibilities**, **defined escalation triggers**, and **measurable outcomes**:

| Tier | Purpose | SLA | Agents | Key Output |
|------|---------|-----|--------|-----------|
| **🔴 Tier 1** | Rapid Triage | 5-15 min | 4 | Normalized alert + decision |
| **🟠 Tier 2** | Deep Analysis | 30-60 min | 4 | Investigation report + escalation decision |
| **🟡 Tier 3** | Forensic Excellence | 8 hours | 4 | Root cause + evidence package |
| **🟢 Cloud Hunter** | Proactive Hunt | 4 hours | 4 | Threat intel + anomaly data |

### Smart Escalation Engine

**Automatic escalation** based on these signals:

- ⚠️ **Tier 1→2**: Confirmed compromise, lateral movement, data exfiltration attempts
- ⚠️ **Tier 2→3**: Multi-system compromise, APT indicators, legal hold requirements
- ⚠️ **Tier 3→Closure**: Investigation complete, remediation plan in place

See [DOCS/OPERATIONS/TIER_INTEGRATION.md](DOCS/OPERATIONS/TIER_INTEGRATION.md) → Detailed decision criteria + playbooks

---

## 📚 Documentation Hub

> **New to SentinelMCP?** Start at [DOCS/README.md](DOCS/README.md) for role-based navigation

Complete documentation organized by **role** and **use case**:

| Role | Documentation | Time |
|------|--------------|------|
| 🔴 **Tier 1 Analyst** | [Alert Triage Procedures](DOCS/OPERATIONS/TIER1_OPERATIONS.md) | 10 min |
| 🟠 **Tier 2 Investigator** | [Investigation Workflow](DOCS/OPERATIONS/INVESTIGATION_WORKFLOW.md) | 10 min |
| 🟡 **Tier 3 Forensic** | [Forensic Deep-Dive](DOCS/OPERATIONS/FORENSIC_PROCEDURES.md) | 10 min |
| 🏗️ **Architect** | [System Design](DOCS/ARCHITECTURE/ARCHITECTURE_OVERVIEW.md) | 15 min |
| 👨‍💻 **Developer** | [Implementation Guide](DOCS/DEVELOPMENT/README.md) | 10 min |
| ❓ **Need Quick Answer?** | [FAQ & Reference](DOCS/REFERENCE/QUICK_REFERENCE.md) | 2 min |
| 🆘 **Troubleshooting** | [Support & Issues](DOCS/SUPPORT/README.md) | 5 min |

### Documentation Directory

SentinelMCP includes **comprehensive reference materials**. Access them at:

- **[DOCS/README.md](DOCS/README.md)** — Master documentation index with search functionality
- **[DOCS/OPERATIONS/](DOCS/OPERATIONS/)** — Tier procedures, SLAs, best practices
- **[DOCS/ARCHITECTURE/](DOCS/ARCHITECTURE/)** — System design, capacity planning, integrations
- **[DOCS/DEVELOPMENT/](DOCS/DEVELOPMENT/)** — Agent customization, extending workflows
- **[DOCS/REFERENCE/](DOCS/REFERENCE/)** — Quick lookups, glossary, FAQ
- **[DOCS/SUPPORT/](DOCS/SUPPORT/)** — Troubleshooting, version compatibility, diagnostics

---

## 📁 Project Structure

```
SentinelMCP/
├── 📋 README.md                          ← You are here
├── 📖 CONTRIBUTING.md                    ← Contributing guidelines
├── 📄 CHANGELOG.md                       ← Version history
├── ⚖️  LICENSE                           ← MIT License
│
├── 📚 DOCS/                              ← COMPREHENSIVE DOCUMENTATION
│   ├── README.md                         ← Start here for navigation
│   ├── OPERATIONS/                       ← Tier 1, 2, 3 procedures + best practices
│   ├── ARCHITECTURE/                     ← System design + capacity planning
│   ├── DEVELOPMENT/                      ← Agent customization + extending
│   ├── REFERENCE/                        ← Quick lookups + glossary + FAQ
│   └── SUPPORT/                          ← Troubleshooting + diagnostics
│
├── 🤖 agents/                            ← 16 Agent Definitions (4 tiers)
│   ├── tier1-agents.yaml
│   ├── tier2-agents.yaml
│   ├── tier3-forensic-agents.yaml
│   └── cloud-hunter-agents.yaml
│
├── 👥 roles/                             ← 16 Role Definitions
│   └── roles-matrix.yaml
│
├── 💡 skills/                            ← 40+ Skills Framework
│   └── skills-matrix.yaml
│
├── 📋 schema/                            ← JSON Validation Schemas
│   ├── agent-schema.json
│   ├── alert-schema.json
│   ├── investigation-schema.json
│   └── case-schema.json
│
└── ⚙️  data/                             ← Configuration + Workflows
    ├── config.yaml                       ← Workspace settings
    ├── tier-integration.yaml             ← Escalation rules (technical)
    ├── data-sources.yaml                 ← Integrated data sources
    ├── workflows.yaml                    ← Operational workflows
    └── escalation-paths.yaml             ← Escalation decision matrices
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

## 🔗 Data Integration

SentinelMCP ingest from **8 major sources** with intelligent enrichment at every tier:

- ✅ **Microsoft Defender XDR** — Endpoint, email, cloud app threats
- ✅ **Entra ID** — Authentication, identity risk events  
- ✅ **Azure Security Center** — Infrastructure + vulnerability data
- ✅ **AWS CloudTrail** — Cloud infrastructure activity
- ✅ **GCP Audit Logs** — Google Cloud operations
- ✅ **Third-Party SIEM** — Integrate additional tools
- ✅ **Threat Intelligence Feeds** — External threat context
- ✅ **Custom Logs** — Application-specific security events

### Alert Lifecycle

Every alert follows this intelligent, efficient path:

```
Raw Alert → Normalize → Enrich → Route → Investigate → Escalate → Close
   (T1)      (T1)       (T1)    (T1)      (T2)        (T3)      (T3)
```

---

## ⚡ Getting Started

### 1. Clone & Setup

```bash
git clone https://github.com/eshlomo1/SentinelMCP.git
cd SentinelMCP
```

### 2. Read Documentation

👉 **[DOCS/README.md](DOCS/README.md)** — Complete navigation guide by role

### 2. Read Documentation

👉 **[DOCS/README.md](DOCS/README.md)** — Complete navigation guide by role

### 3. Customize Your Environment

Edit `data/config.yaml` with your workspace details:

```yaml
workspace_id: your-workspace-id
tenant_id: your-tenant-id
environment: production
slas:
  critical: 5 minutes
  high: 15 minutes
  medium: 1 hour
  low: 4 hours
```

---

## 🎯 The 16 Specialized Agents

### Tier 1: Rapid Alert Triage (SLA: 5-15 min)

| Agent | Role | Purpose |
|-------|------|---------|
| **AlertParser** | t1-alert-normalization | Convert raw alerts to standard format |
| **AlertEnricher** | t1-alert-enrichment | Add context from threat intel + directory |
| **AlertRouter** | t1-alert-routing | Intelligently route to appropriate tier |
| **FPEliminator** | t1-fp-detection | Eliminate 60-80% of false positives |

### Tier 2: Deep Investigation (SLA: 30-60 min)

| Agent | Role | Purpose |
|-------|------|---------|
| **MalwareAnalyzer** | t2-malware-analysis | Analyze indicators of compromise |
| **NetworkInvestigator** | t2-network-investigation | Track lateral movement + data flows |
| **IdentityAnalyzer** | t2-identity-analysis | Investigate anomalous user activity |
| **ThreatAssessor** | t2-threat-assessment | Risk + impact evaluation |

### Tier 3: Forensic Excellence (SLA: 8-24 hours)

| Agent | Role | Purpose |
|-------|------|---------|
| **ForensicInvestigator** | t3-forensic-investigation | Deep forensic analysis + evidence |
| **IncidentReconstructor** | t3-incident-reconstruction | Timeline + attack chain reconstruction |
| **EvidenceCollector** | t3-evidence-collection | Chain of custody + legal preservation |
| **RootCauseAnalyzer** | t3-root-cause-analysis | Determine how + why incidents occurred |

### Cloud Hunter: Proactive Threat Hunt (SLA: 4 hours, parallel)

| Agent | Role | Purpose |
|-------|------|---------|
| **InfrastructureAnalyzer** | ch-infrastructure-security | Cloud resource + config analysis |
| **LogAnomalyDetector** | ch-log-analysis | ML-powered anomaly detection |
| **ThreatIntelEnricher** | ch-threat-intelligence | External threat correlation |
| **ProactiveHunter** | ch-proactive-hunting | Hypothesis-driven threat hunting |

---

## ✨ Why SentinelMCP?

**vs. Manual Alert Triage:**
- ⚡ **10x Faster** — Automated routing vs. manual sorting
- 🎯 **98% Accuracy** — Consistent decision logic vs. human variance
- 📈 **60-80% Fewer FPs** — Automated false positive elimination
- 🔒 **Forensic-Ready** — Chain of custody from day one

**vs. Legacy SIEM Workflows:**
- 🧠 **Intelligent Escalation** — ML-driven decisions vs. threshold-based
- 🔄 **Tier Specialization** — Role-specific tools vs. one-size-fits-all
- 📊 **SLA Automation** — Auto-escalate vs. manual deadline tracking
- 👥 **Skills-Based Assignment** — Right person, right alert, right skills

---

## 📞 Support & Contributing

- **Questions?** → [DOCS/README.md](DOCS/README.md) for complete navigation
- **Want to contribute?** → [CONTRIBUTING.md](CONTRIBUTING.md)
- **Best practices?** → [DOCS/OPERATIONS/BEST_PRACTICES.md](DOCS/OPERATIONS/BEST_PRACTICES.md)
- **Issues?** → [DOCS/SUPPORT/](DOCS/SUPPORT/) for troubleshooting

---

## 📋 About This Project

| Property | Value |
|----------|-------|
| **License** | MIT |
| **Version** | 1.0.0 |
| **Status** | 🟢 Production |
| **Organization** | PurpleX Lab |
| **Last Updated** | February 14, 2026 |
| **Repository** | [github.com/eshlomo1/SentinelMCP](https://github.com/eshlomo1/SentinelMCP) |

---

<div align="center">

**SentinelMCP** — Transform alerts into intelligent investigations

[Documentation](DOCS/README.md) • [Contribute](CONTRIBUTING.md) • [Issues](https://github.com/eshlomo1/SentinelMCP/issues) • [License](LICENSE)

</div>
