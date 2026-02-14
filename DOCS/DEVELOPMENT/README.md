# Development Documentation

Implementation guides for developers, engineers, and system integrators.

## Overview

This directory contains technical guidance for:

- Building new agents
- Integrating external systems
- Customizing workflows
- Extending the framework

## Quick Navigation

### For Implementers

- [Agent Development](AGENT_DEVELOPMENT.md) - Building new agents
- [Integration Guide](INTEGRATION_GUIDE.md) - Connecting systems
- [Workflow Customization](WORKFLOW_CUSTOM.md) - Modifying workflows
- [Schema Guide](SCHEMA_GUIDE.md) - Data validation

### For DevOps/Infrastructure

- [Deployment Guide](DEPLOYMENT.md) - Deploying to your environment
- [Configuration Management](CONFIG_MANAGEMENT.md) - Managing settings
- [Backup & Recovery](BACKUP_RECOVERY.md) - Business continuity

### For Contributors

- [Contributing Guidelines](../../CONTRIBUTING.md) - How to contribute
- [Coding Standards](CODING_STANDARDS.md) - Code style guidelines
- [Testing Guide](TESTING.md) - Writing tests

## Files in This Directory

| File                   | Purpose                  | Audience              |
| ---------------------- | ------------------------ | --------------------- |
| `AGENT_DEVELOPMENT.md` | Building new agents      | Engineers             |
| `INTEGRATION_GUIDE.md` | System integration       | Engineers, Architects |
| `WORKFLOW_CUSTOM.md`   | Customizing workflows    | Engineers             |
| `SCHEMA_GUIDE.md`      | Data validation          | Engineers             |
| `DEPLOYMENT.md`        | Installation & setup     | DevOps, Architects    |
| `CONFIG_MANAGEMENT.md` | Configuration            | DevOps, Engineers     |
| `BACKUP_RECOVERY.md`   | Disaster recovery        | DevOps, Architects    |
| `CODING_STANDARDS.md`  | Code style               | Engineers             |
| `TESTING.md`           | Unit tests & integration | Engineers             |

## Technology Stack

- **Language**: YAML (configuration), Python (implementation), PowerShell (automation)
- **Platform**: Microsoft Sentinel / Azure
- **Data Format**: JSON (schemas), YAML (configuration)
- **Version Control**: Git
- **Documentation**: Markdown

## Quick Start for Developers

### 1. Clone the Repository

```bash
git clone https://github.com/eshlomo1/SentinelMCP.git
cd SentinelMCP
```

### 2. Review Architecture

Read [ARCHITECTURE/](../ARCHITECTURE/ARCHITECTURE_OVERVIEW.md) to understand the system design.

### 3. Choose Your Task

**Building a New Agent?**
→ [Agent Development](AGENT_DEVELOPMENT.md)

**Integrating an External System?**
→ [Integration Guide](INTEGRATION_GUIDE.md)

**Modifying Workflows?**
→ [Workflow Customization](WORKFLOW_CUSTOM.md)

**Deploying to Your Environment?**
→ [Deployment Guide](DEPLOYMENT.md)

### 4. Follow Standards

- Review [Coding Standards](CODING_STANDARDS.md)
- Check [Testing Guide](TESTING.md)
- Read [Contributing Guidelines](../../CONTRIBUTING.md)

## Project Structure for Development

```
SentinelMCP/
├── agents/              ← Agent definitions (YAML)
├── roles/               ← Role definitions (YAML)
├── skills/              ← Skills framework (YAML)
├── schema/              ← JSON validation schemas
├── data/                ← Configuration & procedures
│   └── tier-integration.yaml
├── DOCS/                ← Documentation
└── config.yaml          ← Workspace configuration
```

## Common Development Tasks

### Adding a Custom Data Source

1. Update `data/data-sources.yaml`
2. Test with KQL query
3. Update schema if new fields
4. Document in [INTEGRATION_GUIDE.md](INTEGRATION_GUIDE.md)

### Creating a New Agent

1. Define in appropriate tier YAML
2. Add role in `roles/roles-matrix.yaml`
3. Define success metrics
4. Document in agent YAML
5. See [AGENT_DEVELOPMENT.md](AGENT_DEVELOPMENT.md)

### Customizing Workflows

1. Modify `data/workflows.yaml`
2. Update role mapping
3. Test with sample data
4. See [WORKFLOW_CUSTOM.md](WORKFLOW_CUSTOM.md)

### Adding New Skills

1. Update `skills/skills-matrix.yaml`
2. Map to agents that use them
3. Define success criteria
4. Document in skill definition

## API & Integration Points

### Supported Integrations

- Microsoft Sentinel (KQL queries)
- Azure Automation (PowerShell Runbooks)
- Logic Apps (workflow automation)
- Custom Webhooks (external systems)
- REST APIs (future version)

See [INTEGRATION_GUIDE.md](INTEGRATION_GUIDE.md) for details.

## Testing

All changes should include:

- Unit tests for new functions
- Integration tests with Sentinel
- Documentation updates
- Changelog entry

See [TESTING.md](TESTING.md) for testing framework.

## Support

- Architecture questions? → [ARCHITECTURE/](../ARCHITECTURE/)
- Operations questions? → [OPERATIONS/](../OPERATIONS/)
- Need examples? → Check existing agent YAML files
- Troubleshooting? → [SUPPORT/](../SUPPORT/TROUBLESHOOTING.md)

---

**Last Updated**: February 14, 2026 | **Version**: 1.0.2
