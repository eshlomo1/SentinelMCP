# SENTINEL MCP HIERARCHY - COMPLETE STRUCTURE

Welcome to the PurpleX Lab Sentinel MCP Hierarchy! This is your complete Managed Detection and
Response (MDR) operation structure for Microsoft Sentinel, organized across 4 operational tiers
with 16 agents, 16 roles, 40+ skills, and 5 operational workflows.

# START HERE

1. START: README.md (5 min)
   └─ Overview of the entire hierarchy

2. NEW: TIER_INTEGRATION.md (10 min)
   └─ Escalation between Tier 1, Tier 2, and Tier 3 (Forensic)

3. LEARN: HIERARCHY_SUMMARY.md (10 min)
   └─ Comprehensive summary with all components

4. VISUALIZE: ARCHITECTURE_DIAGRAM.md (5 min)
   └─ Visual diagrams of the hierarchy

5. QUICK: QUICK_REFERENCE.md (3 min)
   └─ Quick reference guide and checklist

# DIRECTORY MAP

SentinelMCP/
├── HIERARCHY_README.md ← Start here!
├── HIERARCHY_SUMMARY.md ← Complete overview
├── ARCHITECTURE_DIAGRAM.md ← Visual diagrams
├── QUICK_REFERENCE.md ← Quick reference
├── INDEX.md ← This file
│
├── config.yaml ← Main configuration
│
├── agents/ ← 16 Agent Definitions
│ ├── tier1-agents.yaml ✓ 4 agents (5-15 min response)
│ ├── tier2-agents.yaml ✓ 4 agents (15-30 min response)  
│ ├── tier3-forensic-agents.yaml ✓ 4 agents (2-8 hour response)
│ └── cloud-hunter-agents.yaml ✓ 4 agents (continuous)
│
├── roles/ ← Role Definitions
│ └── roles-matrix.yaml ✓ 16 roles with responsibilities
│
├── skills/ ← Skill Framework
│ └── skills-matrix.yaml ✓ 40+ skills, 4 progression levels
│
├── schema/ ← Data Schemas (JSON/Validation)
│ ├── agent-schema.json ✓ Agent structure
│ ├── alert-schema.json ✓ Alert standard format
│ ├── investigation-schema.json ✓ Investigation tracking
│ └── case-schema.json ✓ Forensic case records
│
└── data/ ← Operational Data Flows
├── data-sources.yaml ✓ 8 data sources, 5 flow patterns
├── workflows.yaml ✓ 5 workflows with steps & SLAs
└── escalation-paths.yaml ✓ 4 escalation matrices

# WHAT'S INCLUDED

✅ 16 AGENTS (by tier)
• Tier 1 (4): AlertParser, AlertEnricher, AlertRouter, FPEliminator
• Tier 2 (4): MalwareAnalyzer, NetworkInvestigator, IdentityAnalyzer, ThreatAssessor
• Tier 3 (4): ForensicInvestigator, IncidentReconstructor, EvidenceCollector, RootCauseAnalyzer
• Cloud (4): InfrastructureAnalyzer, LogAnomalyDetector, ThreatIntelEnricher, ProactiveHunter

✅ 16 ROLES (mapped to agents)
• Alert Specialists (4)
• Investigation Specialists (4)
• Forensic Experts (4)
• Threat Hunters (4)

✅ 40+ SKILLS (4 levels of progression)
• Core Skills (Level 1-2)
• Investigation Skills (Level 3)
• Forensic Skills (Level 4)
• Cloud Skills (Level 3)
• Technical & Soft Skills

✅ 5 WORKFLOWS (with step-by-step processes)
• Alert to Resolution (10 steps)
• Cloud Threat Hunting (7 steps)
• Escalation Procedures (multiple types)

✅ SLA DEFINITIONS (3 tiers)
• Tier 1: 1-hour response
• Tier 2: 4-hour response
• Tier 3: 24-hour response

✅ 8 DATA SOURCES (integrated)
• Microsoft Defender XDR
• Microsoft Entra ID
• Azure Security Center
• Defender for Cloud Apps
• AWS CloudTrail
• GCP Cloud Audit Logs
• Threat Intelligence Feeds
• Internal Data Stores

✅ 4 JSON SCHEMAS (standard formats)
• Agent Configuration
• Alert Format
• Investigation Records
• Forensic Cases

✅ ESCALATION PATHS (4 matrices)
• Alert Routing
• Investigation Escalation
• Forensic Escalation
• Cloud Hunter Escalation

✅ NOTIFICATION TEMPLATES (3 types)
• Tier 1 to Tier 2 Escalation
• Tier 2 to Tier 3 Escalation
• Critical: Active Breach

# FIND WHAT YOU NEED

Looking for... See...
───────────────────────────── ────────────────────────────────────
Agent definitions agents/ (4 files, 16 agents)
Agent capabilities agents/_.yaml (Capabilities section)
Agent SLA details agents/_.yaml (SLA Response Time)
Agent data sources agents/_.yaml (Data Sources)
Agent integration points agents/_.yaml (Integration Points)

Role definitions roles/roles-matrix.yaml
Role responsibilities roles/roles-matrix.yaml
Role decision authority roles/roles-matrix.yaml
Role escalation authority roles/roles-matrix.yaml

Skill requirements skills/skills-matrix.yaml
Skill progression levels skills/skills-matrix.yaml
Skill by agent skills/skills-matrix.yaml

Alert structure schema/alert-schema.json
Investigation structure schema/investigation-schema.json
Forensic case structure schema/case-schema.json
Agent validation schema schema/agent-schema.json

Data sources data/data-sources.yaml
Data flow patterns data/data-sources.yaml
Workflow steps data/workflows.yaml
Workflow SLAs data/workflows.yaml

Escalation decisions data/escalation-paths.yaml
Escalation criteria data/escalation-paths.yaml
Notification templates data/escalation-paths.yaml
Handoff procedures data/escalation-paths.yaml

Main configuration config.yaml
Organization settings config.yaml
Tier SLAs config.yaml
Response times by severity config.yaml

# TIER OVERVIEW

TIER 1: Alert Triage & Routing (1-hour SLA)
────────────────────────────────────────────
Purpose: Fast triage, normalization, enrichment, and routing of alerts
Agents: 4 (AlertParser, AlertEnricher, AlertRouter, FPEliminator)
Roles: 4 specialists
Response: 5-15 minutes per agent
Key Decision: Route to Tier 2 or suppress
Output: Enriched alert, routing decision

TIER 2: Investigation & Analysis (4-hour SLA)
──────────────────────────────────────────────
Purpose: In-depth investigation and threat assessment
Agents: 4 (Malware, Network, Identity Analytics, Threat Assessment)
Roles: 4 investigators
Response: 15-30 minutes per investigation phase
Key Decision: Confirm incident or false positive
Output: Investigation report, escalation decision

TIER 3: Forensic Analysis (24-hour SLA)
────────────────────────────────────────
Purpose: Deep forensic analysis and root cause determination
Agents: 4 (Forensics, Reconstruction, Evidence, Root Cause)
Roles: 4 forensic experts
Response: 2-8 hours per analysis phase
Key Decision: Root cause, remediation, legal requirements
Output: Forensic report, case documentation

CLOUD THREAT HUNTER: Continuous Proactive Hunting
─────────────────────────────────────────────────
Purpose: Proactive hunting for cloud threats and misconfigurations
Agents: 4 (Infrastructure, Log Analysis, Threat Intel, Proactive Hunt)
Roles: 4 threat hunters
Response: 30 minutes to 4 hours
Key Decision: Escalate findings to Tier 2
Output: Hunting findings, escalated alerts

# HOW TO USE THIS HIERARCHY

STEP 1: Understand the Structure
├─ Read README.md (5 min)
├─ Review HIERARCHY_SUMMARY.md (10 min)
├─ Study ARCHITECTURE_DIAGRAM.md (5 min)
└─ Check QUICK_REFERENCE.md (3 min)

STEP 2: Learn the Agents
├─ Review agents/tier1-agents.yaml
├─ Review agents/tier2-agents.yaml
├─ Review agents/tier3-forensic-agents.yaml
└─ Review agents/cloud-hunter-agents.yaml

STEP 3: Understand Roles & Skills
├─ Study roles/roles-matrix.yaml
└─ Study skills/skills-matrix.yaml

STEP 4: Learn the Data Flow
├─ Review data/data-sources.yaml
├─ Review data/workflows.yaml
└─ Study data/escalation-paths.yaml

STEP 5: Validate Against Schemas
├─ Review schema/agent-schema.json
├─ Review schema/alert-schema.json
├─ Review schema/investigation-schema.json
└─ Review schema/case-schema.json

STEP 6: Implement in Your Environment
├─ Configure data source connections
├─ Set up notification channels
├─ Create escalation procedures
└─ Train your team

# CONFIGURATION SUMMARY

Workspace Details:
ID: 72e316b2-cc46-4d4b-93e1-3561ebae0b82
Tenant: dbf22f42-e951-4d07-8579-1400a6f9a473
Subscription: 4167334c-383c-4f4a-98fa-f4f591d709b3
Organization: PurpleX Lab
Environment: Production

Operational Structure:
Total Agents: 16
Total Roles: 16
Total Skills: 40+
Total Workflows: 5
Total SLAs: 9
Total Escalations: 4
Total Schemas: 4

Key Metrics:
Tier 1 Response: 1 hour
Tier 2 Response: 4 hours
Tier 3 Response: 24 hours
Data Sources: 8
Notification Types: 3
Handoff Procedures: 3

# KEY NAVIGATION LINKS

📚 Documentation
├─ README.md Main overview
├─ HIERARCHY_SUMMARY.md Complete summary
├─ ARCHITECTURE_DIAGRAM.md Visual diagrams
├─ QUICK_REFERENCE.md Quick guide
└─ INDEX.md This file

⚙️ Configuration
└─ config.yaml Main config

👥 People & Responsibilities
├─ roles/roles-matrix.yaml All roles

💪 Capabilities
└─ skills/skills-matrix.yaml All skills

🤖 Automation
├─ agents/tier1-agents.yaml T1 agents
├─ agents/tier2-agents.yaml T2 agents
├─ agents/tier3-forensic-agents.yaml T3 agents
└─ agents/cloud-hunter-agents.yaml Cloud agents

📋 Data Standards
├─ schema/agent-schema.json Agent format
├─ schema/alert-schema.json Alert format
├─ schema/investigation-schema.json Investigation format
└─ schema/case-schema.json Case format

🔄 Operations
├─ data/data-sources.yaml Data sources
├─ data/workflows.yaml Workflows & SLAs
└─ data/escalation-paths.yaml Escalation rules

# LEARNING PATH

Beginner (15 minutes)

1. Read README.md
2. Skim HIERARCHY_SUMMARY.md
3. Look at ARCHITECTURE_DIAGRAM.md

Intermediate (45 minutes)
Previous + :

1. Fully read HIERARCHY_SUMMARY.md
2. Review agents/tier1-agents.yaml
3. Review data/data-sources.yaml

Advanced (2-3 hours)
Previous + :

1. Master all agent definitions (all agents/)
2. Study roles/roles-matrix.yaml
3. Study skills/skills-matrix.yaml
4. Master data flows (data/data-sources.yaml)
5. Master workflows (data/workflows.yaml)
6. Master escalations (data/escalation-paths.yaml)

Expert (4+ hours)
Previous + :

1. Validate all agents against agent-schema.json
2. Understand all schemas deeply
3. Design custom extensions
4. Create implementation plan
5. Train team members

# NEED HELP?

For quick answers:
• Check QUICK_REFERENCE.md for common questions
• Use "Find What You Need" section above
• Look at INDEX.md (this file) navigation

For detailed information:
• Specific agents: Check agents/ directory
• Roles: See roles/roles-matrix.yaml
• Skills: See skills/skills-matrix.yaml

For implementation help:
• Review data/workflows.yaml for step-by-step
• Check data/escalation-paths.yaml for decision points
• Verify schemas for data format validation

---

Version: 1.0.0
Created: February 14, 2026
Org: PurpleX Lab
Env: Production
Status: ✅ Complete & Ready
