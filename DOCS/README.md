# SentinelMCP Documentation

Complete documentation for SentinelMCP MDR framework.

## 🚀 Quick Start

**New to SentinelMCP?** Start here:

1. **[Read the Main README](../README.md)** - High-level overview (5 min)
2. **[Check Quick Reference](REFERENCE/QUICK_REFERENCE.md)** - Fast answers (2 min)
3. **[Review Your Role](#by-role-below)** - Role-specific guides (10 min)

**Already familiar?** Jump to your section:

- [For Operations Teams](#-for-operations-teams) ← Most users start here
- [For Architects](#-for-architects)
- [For Developers](#-for-developers)
- [For Managers](#-for-managers)

---

## 📊 Documentation Map

```
DOCS/
├── README.md (you are here)
├── OPERATIONS/              ← Day-to-day operations
│   ├── README.md
│   ├── TIER_INTEGRATION.md      (START HERE if troubleshooting escalation)
│   ├── TIER1_OPERATIONS.md      (Alert handling)
│   ├── INVESTIGATION_WORKFLOW.md (Tier 2 procedures)
│   ├── FORENSIC_PROCEDURES.md    (Tier 3 procedures)
│   ├── DATA_SOURCES.md           (Available evidence)
│   └── ESCALATION_CHECKLIST.md   (Quick guide)
├── ARCHITECTURE/            ← System design
│   ├── README.md
│   ├── ARCHITECTURE_OVERVIEW.md  (System design)
│   ├── HIERARCHY.md              (Why 4 tiers)
│   ├── DATA_FLOW.md              (How data moves)
│   └── INTEGRATION_POINTS.md     (External systems)
├── DEVELOPMENT/             ← For implementers
│   ├── README.md
│   ├── AGENT_DEVELOPMENT.md      (Building agents)
│   ├── INTEGRATION_GUIDE.md       (Connecting systems)
│   ├── WORKFLOW_CUSTOM.md         (Customizing workflows)
│   └── SCHEMA_GUIDE.md            (Data validation)
├── REFERENCE/               ← Quick lookups
│   ├── README.md
│   ├── QUICK_REFERENCE.md        (2-min cheat sheet)
│   ├── GLOSSARY.md               (Definitions)
│   └── FAQ.md                    (Common questions)
└── SUPPORT/                 ← Help & troubleshooting
    ├── README.md
    ├── TROUBLESHOOTING.md        (Common issues)
    ├── KNOWN_ISSUES.md           (Tracked bugs)
    ├── PERFORMANCE_TUNING.md     (Optimization)
    └── VERSION_COMPATIBILITY.md  (Version support)
```

---

## 👥 By Role

### 👮 **For Operations Teams** (Tier 1, 2, 3 Analysts)

Start here:

1. **[Quick Reference](REFERENCE/QUICK_REFERENCE.md)** (2 min) - Today's cheat sheet
2. **Your Tier Operations** (10 min):
   - Tier 1? → [TIER1_OPERATIONS.md](OPERATIONS/TIER1_OPERATIONS.md)
   - Tier 2? → [INVESTIGATION_WORKFLOW.md](OPERATIONS/INVESTIGATION_WORKFLOW.md)
   - Tier 3? → [FORENSIC_PROCEDURES.md](OPERATIONS/FORENSIC_PROCEDURES.md)
3. **Escalation?** → [ESCALATION_CHECKLIST.md](OPERATIONS/ESCALATION_CHECKLIST.md)

**Common Tasks:**

- Need to escalate? → [Escalation Criteria](REFERENCE/ESCALATION_CRITERIA.md)
- What severity is this? → [Severity Levels](REFERENCE/SEVERITY_LEVELS.md)
- Questions? → [FAQ](FAQ.md)

### 🏗️ **For Architects & Managers**

Start here:

1. **[Architecture Overview](ARCHITECTURE/ARCHITECTURE_OVERVIEW.md)** (10 min) - System design
2. **[Hierarchy Explanation](ARCHITECTURE/HIERARCHY.md)** (5 min) - Why 4 tiers
3. **[Capacity Planning](SUPPORT/CAPACITY_PLANNING.md)** (5 min) - Scaling guidance
4. **[Cost Estimation](SUPPORT/COST_ESTIMATION.md)** (10 min) - Budget planning

**Key Decision Guides:**

- Building this for our org? → [ARCHITECTURE/](ARCHITECTURE/)
- How much will it cost? → [Cost Estimation](SUPPORT/COST_ESTIMATION.md)
- Can we scale this? → [Capacity Planning](SUPPORT/CAPACITY_PLANNING.md)

### 👨‍💻 **For Developers & Engineers**

Start here:

1. **[Development README](DEVELOPMENT/README.md)** (5 min) - Overview
2. **Choose your task:**
   - Building new agent? → [AGENT_DEVELOPMENT.md](DEVELOPMENT/AGENT_DEVELOPMENT.md)
   - Integrating a system? → [INTEGRATION_GUIDE.md](DEVELOPMENT/INTEGRATION_GUIDE.md)
   - Customizing workflows? → [WORKFLOW_CUSTOM.md](DEVELOPMENT/WORKFLOW_CUSTOM.md)
3. **[Contributing Guidelines](../CONTRIBUTING.md)** (5 min) - Before you code

**Useful References:**

- Architecture questions? → [ARCHITECTURE/](ARCHITECTURE/)
- How to validate data? → [Schema Guide](DEVELOPMENT/SCHEMA_GUIDE.md)
- Code standards? → [CODING_STANDARDS.md](DEVELOPMENT/CODING_STANDARDS.md)

### 📊 **For Managers & Leadership**

Start here:

1. **[Architecture Overview](ARCHITECTURE/ARCHITECTURE_OVERVIEW.md)** (10 min) - What is this?
2. **[Hierarchy Explanation](ARCHITECTURE/HIERARCHY.md)** (5 min) - How it works
3. **[Capacity Planning](SUPPORT/CAPACITY_PLANNING.md)** (10 min) - Staffing needs
4. **[Cost Estimation](SUPPORT/COST_ESTIMATION.md)** (10 min) - Budget impact

**Key Metrics:**

- Team size needed? → [CAPACITY_PLANNING.md](SUPPORT/CAPACITY_PLANNING.md)
- Annual cost? → [COST_ESTIMATION.md](SUPPORT/COST_ESTIMATION.md)
- Success metrics? → Check specific tier documentation

---

## 🔍 Search by Topic

### If you're trying to...

| Task                            | Go to                                                      |
| ------------------------------- | ---------------------------------------------------------- |
| **Investigate an alert**        | [OPERATIONS/](OPERATIONS/) → TIER1_OPERATIONS.md           |
| **Decide to escalate**          | [REFERENCE/](REFERENCE/) → ESCALATION_CRITERIA.md          |
| **Understand the architecture** | [ARCHITECTURE/](ARCHITECTURE/) → ARCHITECTURE_OVERVIEW.md  |
| **Build a new agent**           | [DEVELOPMENT/](DEVELOPMENT/) → AGENT_DEVELOPMENT.md        |
| **Find a quick answer**         | [REFERENCE/](REFERENCE/) → QUICK_REFERENCE.md              |
| **Fix an issue**                | [SUPPORT/](SUPPORT/) → TROUBLESHOOTING.md                  |
| **Define a term**               | [REFERENCE/](REFERENCE/) → GLOSSARY.md (or ../GLOSSARY.md) |
| **Plan capacity**               | [SUPPORT/](SUPPORT/) → CAPACITY_PLANNING.md                |
| **Check version support**       | [SUPPORT/](SUPPORT/) → VERSION_COMPATIBILITY.md            |

---

## 📚 Documentation Structure

### OPERATIONS/ (Day-to-Day)

How to actually do the work:

- Tier 1 alert handling
- Tier 2 investigation
- Tier 3 forensics
- Escalation procedures
- Case management

### ARCHITECTURE/ (System Design)

Why and how the system works:

- System architecture
- Component relationships
- Design decisions
- Capacity estimates
- Roadmap

### DEVELOPMENT/ (For Builders)

How to extend and customize:

- Building agents
- Integrating systems
- Customizing workflows
- Data validation
- Testing

### REFERENCE/ (Quick Lookup)

Fast answers without reading:

- 2-minute cheat sheet
- Decision tables
- Glossary
- FAQ

### SUPPORT/ (Help & Troubleshooting)

When something goes wrong:

- Troubleshooting guide
- Known issues
- Performance tuning
- Version compatibility

---

## 🎯 Common Workflows

### "I have an alert - what do I do?"

1. Check severity → [Severity Levels](REFERENCE/SEVERITY_LEVELS.md)
2. Follow Tier 1 procedures → [TIER1_OPERATIONS.md](OPERATIONS/TIER1_OPERATIONS.md)
3. Decide: Escalate or close? → [Escalation Criteria](REFERENCE/ESCALATION_CRITERIA.md)

**Estimated time: 5-15 minutes**

### "I need to investigate further"

1. Follow Tier 2 procedures → [INVESTIGATION_WORKFLOW.md](OPERATIONS/INVESTIGATION_WORKFLOW.md)
2. Collect evidence → [DATA_SOURCES.md](OPERATIONS/DATA_SOURCES.md)
3. Decide: Escalate to Tier 3? → [TIER_INTEGRATION.md](OPERATIONS/TIER_INTEGRATION.md)

**Estimated time: 30-60 minutes**

### "I have a serious incident"

1. Escalate to Tier 3 → [TIER_INTEGRATION.md](OPERATIONS/TIER_INTEGRATION.md)
2. Follow forensic procedures → [FORENSIC_PROCEDURES.md](OPERATIONS/FORENSIC_PROCEDURES.md)
3. Manage case documentation → [CASE_MANAGEMENT.md](OPERATIONS/CASE_MANAGEMENT.md)

**Estimated time: 4-24 hours**

### "I want to customize this system"

1. Understand the architecture → [ARCHITECTURE/](ARCHITECTURE/)
2. Choose what to customize → [DEVELOPMENT/](DEVELOPMENT/)
3. Read the development guide for that component
4. Review [CONTRIBUTING.md](../CONTRIBUTING.md) before submitting

**Estimated time: varies by task**

---

## 🔗 Cross-References

- **Need operations help?** → [OPERATIONS/](OPERATIONS/)
- **Need architecture help?** → [ARCHITECTURE/](ARCHITECTURE/)
- **Need development help?** → [DEVELOPMENT/](DEVELOPMENT/)
- **Need quick answer?** → [REFERENCE/](REFERENCE/)
- **Having a problem?** → [SUPPORT/](SUPPORT/)
- **Have a question?** → [FAQ](FAQ.md)
- **Don't know a term?** → [GLOSSARY](GLOSSARY.md)

---

## 📖 How to Read This Documentation

### If you have 5 minutes

→ Read [Quick Reference](REFERENCE/QUICK_REFERENCE.md)

### If you have 15 minutes

→ Read:

1. [Main README](../README.md)
2. [QUICK_REFERENCE.md](REFERENCE/QUICK_REFERENCE.md)

### If you have 1 hour

→ Read:

1. [Architecture Overview](ARCHITECTURE/ARCHITECTURE_OVERVIEW.md)
2. Your specific role sections
3. [TIER_INTEGRATION.md](OPERATIONS/TIER_INTEGRATION.md)

### If you have a day

→ Read:

1. [Main README](../README.md)
2. All of [ARCHITECTURE/](ARCHITECTURE/)
3. Your tier-specific [OPERATIONS/](OPERATIONS/) docs
4. Skim all [REFERENCE/](REFERENCE/) docs

---

## 📝 Contributing to Documentation

Found an error? Want to improve docs?
→ See [Contributing Guidelines](../CONTRIBUTING.md)

---

## 🆘 Getting Help

1. **Quick answer?** → [QUICK_REFERENCE.md](REFERENCE/QUICK_REFERENCE.md)
2. **Something broken?** → [TROUBLESHOOTING.md](SUPPORT/TROUBLESHOOTING.md)
3. **Have a question?** → [FAQ.md](FAQ.md)
4. **Not finding it?** → File an issue on [GitHub](https://github.com/eshlomo1/SentinelMCP/issues)

---

**Last Updated**: February 14, 2026 | **Version**: 1.0.2  
**Repository**: [github.com/eshlomo1/SentinelMCP](https://github.com/eshlomo1/SentinelMCP)
