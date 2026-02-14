# Architecture Documentation

System design, hierarchy explanation, and architectural decisions for SentinelMCP.

## Overview

This directory contains high-level architecture documentation for architects, engineers, and developers implementing or customizing SentinelMCP.

## Quick Navigation

### Understanding the System

- [Architecture Overview](ARCHITECTURE_OVERVIEW.md) - System design and components
- [Hierarchy Explanation](HIERARCHY.md) - Why 4 tiers and how they work
- [Data Flow Diagram](DATA_FLOW.md) - How data moves through the system
- [Integration Points](INTEGRATION_POINTS.md) - Where to connect external systems

### Capacity & Performance

- [Capacity Planning](CAPACITY_PLANNING.md) - Scaling the system
- [Performance Tuning](PERFORMANCE_TUNING.md) - Optimization guide
- [Cost Analysis](COST_ANALYSIS.md) - Estimate operational costs

### Design Decisions

- [Design Rationale](DESIGN_RATIONALE.md) - Why we chose this architecture
- [Trade-offs](TRADEOFFS.md) - What we sacrificed for what we gained
- [Future Roadmap](ROADMAP.md) - Planned enhancements

## Files in This Directory

| File                       | Purpose                      | Audience               |
| -------------------------- | ---------------------------- | ---------------------- |
| `ARCHITECTURE_OVERVIEW.md` | System design and components | Architects, Engineers  |
| `HIERARCHY.md`             | 4-tier structure explanation | Architects, Managers   |
| `DATA_FLOW.md`             | Data movement through system | Engineers, Architects  |
| `INTEGRATION_POINTS.md`    | External system connections  | Engineers, Integrators |
| `CAPACITY_PLANNING.md`     | Scaling guidance             | Architects, Managers   |
| `PERFORMANCE_TUNING.md`    | Optimization guide           | Engineers              |
| `COST_ANALYSIS.md`         | Budget estimation            | Managers, Finance      |
| `DESIGN_RATIONALE.md`      | Why this design              | Architects             |

## Key Architectural Principles

### 1. **Separation of Concerns** (4 Tiers)

Each tier has specific responsibilities with clear boundaries.

### 2. **Automation-First**

Automatic escalation, decision-making, and workflow execution where possible.

### 3. **Evidence Preservation**

Chain of custody maintained throughout investigation lifecycle.

### 4. **Scalability**

Designed to handle organizations from 100 to 10,000+ users.

### 5. **Auditability**

All decisions logged and traceable for compliance.

## Tier Architecture

```
┌─────────────────────────────────────────┐
│  DATA SOURCES                           │
│  (Defender, Entra, Azure, AWS, GCP)    │
└──────────┬──────────────────────────────┘
           │
           ▼
┌──────────────────────┐     ┌──────────────────┐
│  TIER 1: TRIAGE      │     │  CLOUD HUNTER    │
│  (4 agents)          │     │  (Parallel, 4)   │
│  SLA: 5-15 min       │     │  SLA: 4 hours    │
└──────────┬───────────┘     └──────────────────┘
           │
           ▼
┌──────────────────────┐
│  TIER 2: INVESTIGATE │
│  (4 agents)          │
│  SLA: 30-60 min      │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│  TIER 3: FORENSIC    │
│  (4 agents)          │
│  SLA: 8-24 hours     │
└──────────┬───────────┘
           │
           ▼
    ┌─────────────┐
    │  RESOLUTION │
    │  & CLOSURE  │
    └─────────────┘
```

## Capacity Estimates

| Metric             | Small Org | Medium Org | Large Org |
| ------------------ | --------- | ---------- | --------- |
| Users              | 100       | 1,000      | 10,000    |
| Tier 1 Alerts/Day  | 500       | 5,000      | 50,000    |
| Tier 2 Cases/Week  | 10        | 100        | 200       |
| Tier 3 Cases/Month | 5         | 20         | 50        |
| Analysts Needed    | 2-3       | 4-5        | 8-10      |

See [Capacity Planning](CAPACITY_PLANNING.md) for details.

## Design Rationale

### Why 4 Tiers?

1. **Tier 1 (Triage)** - Reduces alert noise from thousands to potentially risky (5%)
2. **Tier 2 (Investigation)** - Confirms threat and determines scope (20-30% escalation)
3. **Tier 3 (Forensic)** - Deep analysis for confirmed incidents (5-10% escalation)
4. **Cloud Hunter (Parallel)** - Proactive hunting independent of alert queue

This creates an efficient funnel where each tier adds more depth.

### Why Automatic Escalation?

- **Speed**: No manual approval bottleneck
- **Consistency**: Same rules applied every time
- **Auditability**: Clear triggers documented
- **SLA Compliance**: Deadlines respected automatically

## Support

- Need implementation details? See [DEVELOPMENT/](../DEVELOPMENT/)
- Questions? Check [FAQ](../FAQ.md)
- Troubleshooting? See [SUPPORT/](../SUPPORT/)

---

**Last Updated**: February 14, 2026 | **Version**: 1.0.2
