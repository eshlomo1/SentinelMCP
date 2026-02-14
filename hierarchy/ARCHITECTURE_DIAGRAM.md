# Sentinel MCP Hierarchy Architecture

## Visual Architecture

```
┌────────────────────────────────────────────────────────────────────────────────┐
│                        SENTINEL MCP HIERARCHY                                  │
│                    PurpleX Lab - Microsoft Sentinel                            │
└────────────────────────────────────────────────────────────────────────────────┘

┌────────────────────────────────────────────────────────────────────────────────┐
│                           DATA SOURCES                                         │
├────────────────────────────────────────────────────────────────────────────────┤
│ • Defender XDR      • Entra ID         • Azure Security      • Cloud Apps      │
│ • AWS CloudTrail    • GCP Audit Logs   • Threat Intel Feeds  • Internal DBs    │
└────────────────────────────────────────────────────────────────────────────────┘
                                    ▼
┌──────────────────────────────────────────────────────────────────────────────────┐
│ TIER 1: ALERT TRIAGE & ROUTING (SLA: 1 Hour)                                    │
├──────────────────────┬─────────────────────┬──────────────────┬────────────────┤
│  AlertParser         │ AlertEnricher       │ AlertRouter      │  FPEliminator  │
│  ────────────────    │ ─────────────────   │ ───────────────  │  ────────────  │
│ • Parse              │ • Enrich with TI    │ • Route findings │ • Detect FP    │
│ • Normalize          │ • Add context       │ • Assess severity│ • Filter noise │
│ • Validate           │ • Historical lookup │ • Escalate to T2 │ • Suppress     │
│ SLA: 5 min           │ SLA: 2 min          │ SLA: 1 min       │ SLA: 30 sec    │
└──────────────────────┴─────────────────────┴──────────────────┴────────────────┘
                                    ▼
        ┌───────────────────┬──────────────────┬───────────────────┐
        │  Escalation Paths  │  Continue        │   Cloud Hunting   │
        │  (Critical/High)   │  Monitoring      │   (Parallel)      │
        │  30 min - 4 hrs    │  (Medium/Low)    │                   │
        ▼                    ▼                  ▼                   ▼
┌────────────────────┐  │  ┌──────────────────────────────────────────────┐
│INVESTIGATION QUEUE │  │  │ CLOUD THREAT HUNTER (Continuous)             │
└────────────────────┘  │  ├──────────────────────────────────────────────┤
       │                │  │ • InfrastructureAnalyzer (2 hrs)             │
       │                │  │ • LogAnomalyDetector (30 min)                │
       ▼                │  │ • ThreatIntelEnricher (1 hr)                 │
┌──────────────────────────────────────────────────────────────────────────────┐
│ TIER 2: INVESTIGATION & ANALYSIS (SLA: 4 Hours)                              │
├──────────────────────┬───────────────────┬─────────────────┬────────────────┤
│ MalwareAnalyzer      │ NetworkInvestigator│ IdentityAnalyzer│ ThreatAssessor  │
│ ─────────────────    │ ──────────────────  │ ────────────────│ ────────────   │
│ • File analysis      │ • Network flows     │ • Auth analysis │ • Severity     │
│ • Process behavior   │ • DNS investigation │ • Privesc detect│ • Impact       │
│ • Sandbox analysis   │ • C2 detection      │ • Account risk  │ • Escalate to  │
│ • Malware family     │ • Lateral movement  │ • User profiling│   T3           │
│ SLA: 30 min          │ SLA: 20 min         │ SLA: 15 min     │ SLA: 25 min    │
└──────────────────────┴───────────────────┴─────────────────┴────────────────┘
        │                   │                   │                   │
        └───────────────────┴───────────────────┴───────────────────┘
                            ▼
            ┌─── Escalation (Confirmed Incident) ───┐
            │         (2-24 hours)                    │
            ▼                                          ▼
┌──────────────────────────────────────────────────────────────────────────────┐
│ TIER 3: FORENSIC ANALYSIS (SLA: 24 Hours)                                    │
├──────────────────────┬───────────────────┬─────────────────┬────────────────┤
│ EvidenceCollector    │ ForensicInvestigator│IncidentReconst │ RootCauseAnalyz│
│ ──────────────────   │ ───────────────────  │ ──────────────  │ ──────────────│
│ • Preserve evidence  │ • Memory forensics  │ • Timeline       │ • Root cause  │
│ • Chain of custody   │ • Disk forensics    │ • Event correlat│ • Contributing│
│ • Hash verification  │ • Artifact analysis │ • Causality      │ • Attack tech │
│ • Legal compliance   │ • Registry analysis │ • Attack path   │ • Remediation │
│ SLA: 2 hours         │ SLA: 4 hours        │ SLA: 6 hours    │ SLA: 8 hours  │
└──────────────────────┴───────────────────┴─────────────────┴────────────────┘
            │                   │                   │                   │
            └───────────────────┴───────────────────┴───────────────────┘
                                ▼
                    ┌─────────────────────────┐
                    │  FINAL REPORT & CLOSURE │
                    │  • Root Cause Documented│
                    │  • Evidence Preserved   │
                    │  • Lessons Learned      │
                    │  • Recommendations      │
                    └─────────────────────────┘
                                ▼
        ┌───────────────────────────────────────────┐
        │  Legal Review (if applicable)             │
        │  Notification (if required)               │
        │  Remediation Implementation               │
        └───────────────────────────────────────────┘


## Decision Flow

                            ┌─────────────────────┐
                            │   Alert Received    │
                            └──────────┬──────────┘
                                       ▼
                       ┌───────────────────────────────┐
                       │  Tier 1: Parse & Normalize    │
                       └──────────┬────────────────────┘
                                  ▼
                       ┌───────────────────────────────┐
                       │  Tier 1: Enrich & Classify    │
                       └──────────┬────────────────────┘
                                  ▼
                       ┌───────────────────────────────┐
                       │  Tier 1: False Positive Check?│
                       └──────┬────────────────┬───────┘
                N_________|                    |_________Y
               │                                       │
          Investigate                            Archive as FP
               │
               ▼
      ┌────────────────┐
      │ Severity Check │
      └────┬──────┬────┘
           │      │
      Critical/High  Medium/Low
           │           │
           ▼           ▼
    ┌──────────────┐ Monitor
    │ Tier 2       │
    │ Investigation│
    └──────┬───────┘
           │
           ▼
    ┌─────────────────┐
    │ Confirmed       │
    │ Incident?       │
    └──┬──────────┬───┘
       │Y         │N
       ▼          └─→ Close
    ┌──────────────┐
    │ Tier 3       │
    │ Forensics    │
    └──────┬───────┘
           │
           ▼
    ┌──────────────┐
    │ Final Report │
    │ & Closure    │
    └──────────────┘


## Role Hierarchy

                        ┌─────────────────┐
                        │  CISO / SEER    │
                        └────────┬────────┘
                                 │
                ┌────────────────┼────────────────┐
                │                │                │
        ┌──────▼────────┐ ┌──────▼───────┐ ┌──────▼────────┐
        │ SOC Director  │ │ Case Manager │ │ Legal Counsel │
        └──────┬────────┘ └──────┬───────┘ └──────┬────────┘
               │                 │                 │
      ┌────────┴──────┐    ┌─────┴────────┐       │
      │                │    │              │       │
  ┌───▼──────┐   ┌────▼─┐ ┌─┴──────┐      │       │
  │ Tier 1   │   │Tier2 │ │Tier 3  │      │       │
  │Manager   │   │Lead  │ │Lead    │      │       │
  └───┬──────┘   └────┬─┘ └─┬──────┘      │       │
      │               │      │             │       │
   ┌──┴──┬──┬────┐    │    ┌─┴──┬──┬────┐ │       │
   │Analysts  │    │      │Invest  │      │Forensic│
   │Parsers   │    │      │Analysts│      │Experts │
   │Enrichers │    │      │        │      │        │
   │Routers   │    │      │        │      │        │
   └─────────┘    │      └────────┘      │        │
                  └─────────────────────┘         │
                         │                         │
                         └────────────┬────────────┘
                                      ▼
                        ┌──────────────────────┐
                        │ Cloud Threat Hunter  │
                        │ (Parallel Operation) │
                        └──────────────────────┘

## Skills Progression

    Level 1: Analyst        Level 2: Senior Analyst    Level 3: Investigator    Level 4: Expert
    ───────────────        ──────────────────────     ───────────────────     ──────────────
    • Alert Parsing         • TI Integration           • Malware Analysis      • Forensic Analysis
    • Normalization         • Classification           • Network Analysis      • Windows Internals
    • Pattern Recognition   • Query Optimization       • Identity Analysis     • Root Cause Analysis
                           • Basic Enrichment          • Risk Assessment       • Incident Reconstruction
                                                       • Threat Hunting        • Evidence Preservation


## Integration Points

            ┌─────────────────────────────────────────────────────────────┐
            │           External Systems & Integrations                   │
            ├─────────────────────────────────────────────────────────────┤
            │                                                              │
      ┌─────▼─────┐   ┌──────────────┐   ┌──────────────┐   ┌──────────┐ │
      │   SIEM     │   │ Threat Intel │   │ Cloud Config │   │  Legal   │ │
      │  Systems   │   │   Platforms  │   │  Management  │   │ Systems  │ │
      └────────────┘   └──────────────┘   └──────────────┘   └──────────┘ │
      │                                                                      │
      ├──────────────────────────── Sentinel MCP ────────────────────────────┤
      │                                                                      │
      ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌───────────┐  │
      │  IT Systems  │  │ Communication│  │ Evidence Mgmt│  │  Compliance
      │  SOAR/ITMS   │  │ (Teams/Slack)│  │   Systems    │  │  Systems  │  │
      └──────────────┘  └──────────────┘  └──────────────┘  └───────────┘  │
            │                                                                 │
            └─────────────────────────────────────────────────────────────────┘
```

## Component Relationships

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         COMPONENT MAP                                       │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  AGENTS (16)          ROLES (16)          SKILLS (40+)      SCHEMAS (4)    │
│  ├─ 4 Tier 1         ├─ 4 Tier 1         ├─ Core (5)       ├─ Agent       │
│  ├─ 4 Tier 2         ├─ 4 Tier 2         ├─ Investigation  ├─ Alert       │
│  ├─ 4 Tier 3         ├─ 4 Tier 3         ├─ Forensic       ├─ Investigation
│  └─ 4 Cloud Hunter   └─ 4 Cloud Hunter   ├─ Cloud          └─ Case        │
│                                           ├─ Technical       DATA SOURCES   │
│  WORKFLOWS (5)        ESCALATION (4)      └─ Soft Skills     (8)           │
│  ├─ Alert to Closure  ├─ T1 to T2                          ├─ Defender    │
│  ├─ Cloud Hunting     ├─ T2 to T3         SLAs (3)         ├─ Entra ID    │
│  ├─ Investigation     ├─ Cloud to T2      ├─ Tier 1        ├─ Azure       │
│  ├─ Forensics         └─ Critical Response├─ Tier 2        ├─ Cloud Apps  │
│  └─ Remediation                           └─ Tier 3        ├─ AWS         │
│                                                              ├─ GCP         │
│                       NOTIFICATIONS       HANDOFF           ├─ Threat TI   │
│                       ├─ Email            ├─ T1 to T2      └─ Internal    │
│                       ├─ Slack            ├─ T2 to T3      Templates (3)  │
│                       ├─ Teams            └─ T3 to Legal   ├─ T1 to T2   │
│                       ├─ SMS              Procedures       ├─ T2 to T3   │
│                       └─ Phone                             └─ T3 to Legal │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

## File Organization Matrix

```
hierarchy/
├── README.md                    # Start here - overview
├── HIERARCHY_SUMMARY.md        # This file - architecture
├── ARCHITECTURE_DIAGRAM.md     # Visual diagrams
├── config.yaml                  # Main config
│
├── agents/                      # 16 Agent definitions
│   ├── tier1-agents.yaml       # 4 agents
│   ├── tier2-agents.yaml       # 4 agents
│   ├── tier3-forensic-agents.yaml # 4 agents
│   └── cloud-hunter-agents.yaml  # 4 agents
│
├── roles/                       # Role definitions
│   └── roles-matrix.yaml       # 16 roles
│
├── skills/                      # Skill definitions
│   └── skills-matrix.yaml      # 40+ skills, 4 levels
│
├── schema/                      # Data schemas
│   ├── agent-schema.json
│   ├── alert-schema.json
│   ├── investigation-schema.json
│   └── case-schema.json
│
└── data/                        # Data flows
    ├── data-sources.yaml       # 8 sources, 5 patterns
    ├── workflows.yaml          # 5 workflows, SLAs
    └── escalation-paths.yaml   # 4 escalation matrices
```

---

**Created**: February 14, 2026
**Version**: 1.0.0
