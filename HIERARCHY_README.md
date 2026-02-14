# Sentinel MCP Hierarchy

Comprehensive hierarchy for Managed Detection and Response (MDR) operations using Model Context Protocol (MCP) agents.

## Organization Structure

The Sentinel MCP hierarchy organizes security operations across four operational tiers:

- **MDR Tier 1**: Initial triage, alert routing, basic enrichment
- **MDR Tier 2**: In-depth investigation, malware analysis, threat assessment
- **Forensic (Tier 3)**: Deep forensic analysis, incident reconstruction, evidence preservation
- **Cloud Threat Hunter**: Proactive cloud infrastructure hunting, threat intelligence integration

## Directory Structure

```
SentinelMCP/
├── config.yaml                    # Main configuration
├── agents/                        # Agent definitions
│   ├── tier1-agents.yaml
│   ├── tier2-agents.yaml
│   ├── tier3-forensic-agents.yaml
│   └── cloud-hunter-agents.yaml
├── roles/                         # Role definitions and responsibilities
│   └── roles-matrix.yaml
├── skills/                        # Skills and capabilities
│   └── skills-matrix.yaml
├── schema/                        # Data schemas
│   ├── agent-schema.json
│   ├── alert-schema.json
│   ├── investigation-schema.json
│   └── case-schema.json
└── data/                          # Data flows and sources
    ├── data-sources.yaml
    ├── workflows.yaml
    └── escalation-paths.yaml
```

## Agent Hierarchy

### Tier 1 - Alert Triage & Routing

- **Tier1-AlertParser**: Parses and normalizes incoming alerts
- **Tier1-AlertEnricher**: Enriches alerts with context and historical data
- **Tier1-AlertRouter**: Routes alerts to appropriate teams/tiers
- **Tier1-FalsePositiveEliminator**: Identifies and filters false positives

### Tier 2 - Investigation & Analysis

- **Tier2-MalwareAnalyzer**: Analyzes suspicious files and processes
- **Tier2-NetworkInvestigator**: Investigates network anomalies
- **Tier2-IdentityAnalyzer**: Analyzes authentication and identity risks
- **Tier2-ThreatAssessor**: Assesses threat severity and impact

### Tier 3 - Forensic Analysis

- **Tier3-ForensicInvestigator**: Deep forensic investigation
- **Tier3-IncidentReconstructor**: Reconstructs incident timeline
- **Tier3-EvidenceCollector**: Collects and preserves evidence
- **Tier3-RootCauseAnalyzer**: Determines root cause

### Cloud Threat Hunter

- **CloudHunter-InfrastructureAnalyzer**: Analyzes cloud infrastructure for misconfigurations
- **CloudHunter-LogaAnomalyDetector**: Detects anomalies in cloud logs
- **CloudHunter-ThreatIntelligenceEnricher**: Integrates threat intelligence
- **CloudHunter-ProactiveHunter**: Proactively hunts for threats

## Key Interactions

1. **Alert Flow**: Tier1 → Tier2 → Tier3 (as escalation)
2. **Data Sharing**: All tiers share common alert/case schema
3. **Skill Delegation**: Agents call specialized skills based on incident type
4. **Investigation Handoff**: Tier2 escalates to Tier3 for forensic needs
5. **Cloud Integration**: CloudHunter operates in parallel, feeds findings to Tier2

## See Also

- [Agent Definitions](agents/)
- [Roles Matrix](roles/roles-matrix.yaml)
- [Skills Matrix](skills/skills-matrix.yaml)
- [Schemas](schema/)
- [Data Flows](data/)
