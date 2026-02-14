# Reference Documentation

Quick lookups, FAQs, and terminology for SentinelMCP.

## Overview

This directory contains quick-reference materials for rapid lookup without needing to read full procedural documents.

## Quick Navigation

### Quick Answers

- [Quick Reference](QUICK_REFERENCE.md) - 2-minute cheat sheet
- [FAQ](../FAQ.md) - Common questions
- [Glossary](../GLOSSARY.md) - Terminology and definitions

### Lookup Tables

- [Severity Levels](SEVERITY_LEVELS.md) - How we rate alert severity
- [Escalation Criteria](ESCALATION_CRITERIA.md) - When to escalate
- [Agent Capabilities](AGENT_CAPABILITIES.md) - What each agent does
- [Role Authority Matrix](ROLE_AUTHORITY.md) - Who can decide what

## Files in This Directory

| File                     | Purpose                   | Use When                     |
| ------------------------ | ------------------------- | ---------------------------- |
| `QUICK_REFERENCE.md`     | 2-minute cheat sheet      | You need a fast answer       |
| `SEVERITY_LEVELS.md`     | Alert severity guide      | Determining alert severity   |
| `ESCALATION_CRITERIA.md` | Escalation decision table | Deciding whether to escalate |
| `AGENT_CAPABILITIES.md`  | What agents can do        | Understanding agent roles    |
| `ROLE_AUTHORITY.md`      | Decision authority matrix | Who can make what decisions  |

## Common Quick Lookups

### "When do I escalate to Tier 2?"

Check [ESCALATION_CRITERIA.md](ESCALATION_CRITERIA.md) or use this quick guide:

- 🔴 **CRITICAL severity** → Escalate immediately (0-5 min)
- 🟠 **HIGH severity** + evidence → Escalate (1-4 hours)
- 🟡 **MEDIUM severity** + pattern → Consider escalating
- 🟢 **LOW severity** → Usually close if no risk

Full details: [TIER_INTEGRATION.md](../OPERATIONS/TIER_INTEGRATION.md)

### "What's my SLA response time?"

Check the table below or [QUICK_REFERENCE.md](QUICK_REFERENCE.md):

| Severity | Tier 1 | Tier 2  | Tier 3   |
| -------- | ------ | ------- | -------- |
| Critical | 30 sec | 5 min   | 1 hour   |
| High     | 2 min  | 15 min  | 4 hours  |
| Medium   | 5 min  | 30 min  | 8 hours  |
| Low      | 15 min | 4 hours | 24 hours |

### "What does this agent do?"

Check [AGENT_CAPABILITIES.md](AGENT_CAPABILITIES.md) or search:

- [agents/tier1-agents.yaml](/agents/tier1-agents.yaml)
- [agents/tier2-agents.yaml](/agents/tier2-agents.yaml)
- [agents/tier3-forensic-agents.yaml](/agents/tier3-forensic-agents.yaml)
- [agents/cloud-hunter-agents.yaml](/agents/cloud-hunter-agents.yaml)

### "What term is that?"

Check [Glossary](../GLOSSARY.md) for all terminology definitions.

### "I have a question that's not answered here"

1. Check [FAQ](../FAQ.md) - Most questions are answered
2. Review [QUICK_REFERENCE.md](QUICK_REFERENCE.md)
3. Search [GLOSSARY](../GLOSSARY.md)
4. Check the specific tier documentation
5. If still stuck, file an issue on GitHub

## How to Use This Directory

### For Quick Answers

- Go to [QUICK_REFERENCE.md](QUICK_REFERENCE.md)
- Takes 2-3 minutes to scan

### For Escalation Decision

- Go to [ESCALATION_CRITERIA.md](ESCALATION_CRITERIA.md)
- Clear decision table

### For Understanding Agent Roles

- Go to [AGENT_CAPABILITIES.md](AGENT_CAPABILITIES.md)
- See what each agent does

### For Authority Questions

- Go to [ROLE_AUTHORITY.md](ROLE_AUTHORITY.md)
- Clear authority matrix

### For Definitions

- Go to [GLOSSARY](../GLOSSARY.md)
- Alphabetical list of all terms

## Tips for Using Reference Materials

1. **Bookmark this page** - You'll come back often
2. **Use browser search (Ctrl+F)** - Fast lookup in cheat sheet
3. **Reference by severity** - Most decisions key off severity
4. **Cross-reference escalation table** - It covers 90% of decisions
5. **Keep glossary handy** - For unfamiliar terms

## Document Relationships

```
QUICK_REFERENCE.md
  ├─ Severity Levels → SEVERITY_LEVELS.md
  ├─ Escalation → ESCALATION_CRITERIA.md
  ├─ Agents → AGENT_CAPABILITIES.md
  ├─ Authority → ROLE_AUTHORITY.md
  └─ Definitions → ../GLOSSARY.md

FAQ.md
  ├─ Procedures → ../OPERATIONS/
  └─ Technical → ../ARCHITECTURE/

GLOSSARY.md
  └─ All terminology
```

## Integration with Other Docs

- **Operations need clarification?** → [OPERATIONS/](../OPERATIONS/)
- **Architecture questions?** → [ARCHITECTURE/](../ARCHITECTURE/)
- **Development questions?** → [DEVELOPMENT/](../DEVELOPMENT/)
- **Troubleshooting?** → [SUPPORT/](../SUPPORT/)

---

**Last Updated**: February 14, 2026 | **Version**: 1.0.2
