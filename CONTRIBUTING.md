# Contributing to SentinelMCP

Thank you for your interest in contributing to SentinelMCP! This document provides guidelines and instructions for contributing to the project.

## Overview

SentinelMCP is a comprehensive Managed Detection and Response (MDR) framework for Microsoft Sentinel. Contributions help improve the framework for all users across the PurpleX Lab security operations.

## Code of Conduct

- Be respectful and professional
- Focus on the issue or improvement, not the person
- Provide constructive feedback
- Help others learn and grow

## Getting Started

### 1. Understand the Structure

Familiarize yourself with the project structure:

```
hierarchy/
├── agents/          # Agent definitions (16 agents, 4 tiers)
├── roles/           # Role definitions (16 roles)
├── skills/          # Skills framework (40+ skills)
├── schema/          # JSON validation schemas (4 files)
└── data/            # Configuration and workflows
```

### 2. Review Documentation

Before making changes, review:

- [README.md](README.md) - Project overview
- [HIERARCHY_README.md](HIERARCHY_README.md) - Hierarchy overview
- [HIERARCHY_SUMMARY.md](HIERARCHY_SUMMARY.md) - Complete documentation
- [ARCHITECTURE_DIAGRAM.md](ARCHITECTURE_DIAGRAM.md) - Architecture
- [INDEX.md](INDEX.md) - Navigation index

## Types of Contributions

### Bug Reports

Report bugs by creating an issue with:

- **Title**: Clear, concise description
- **Description**: What went wrong and expected behavior
- **Steps to Reproduce**: How to reproduce the issue
- **Environment**: Workspace ID, data sources affected
- **Screenshots**: If applicable

### Feature Requests

Request features with:

- **Title**: Clear description of the feature
- **Motivation**: Why this feature would be useful
- **Proposed Solution**: How it should work
- **Alternative Solutions**: Other approaches considered

### Documentation Improvements

Improve documentation by:

- Clarifying existing content
- Adding examples or use cases
- Fixing errors or typos
- Creating new guides

### Code/Configuration Changes

Contribute agent definitions, workflows, or configurations by:

- Creating or modifying YAML/JSON files
- Ensuring files follow existing structure
- Adding validation against schemas
- Testing with actual data

## Contribution Process

### 1. Fork and Clone

```bash
git clone https://github.com/eshlomo1/SentinelMCP.git
cd SentinelMCP
```

### 2. Create a Branch

```bash
git checkout -b feature/your-feature-name
# or for bug fixes
git checkout -b fix/bug-description
```

### 3. Make Changes

#### For Agent Definitions

- Follow the structure in `agents/*.yaml`
- Include: id, role_id, name, role, description, capabilities, data_sources, skills, sla_response_time, success_metrics
- Ensure role_id matches an existing role in `roles/roles-matrix.yaml`
- Add skills that exist in `skills/skills-matrix.yaml`

#### For Role Definitions

- Follow the structure in `roles/roles-matrix.yaml`
- Include: role_id, role_name, primary_agent, responsibilities, required_skills, decision_authority, escalation_authority

#### For Skill Definitions

- Follow the structure in `skills/skills-matrix.yaml`
- Include: skill_id, skill_name, level, category, description, agents_using, difficulty, sub_skills

#### For Workflows

- Add to `data/workflows.yaml`
- Include: workflow_id, name, description, steps (with inputs, actions, outputs), sla, escalation_criteria

#### For Documentation

- Use Markdown format
- Follow existing style and structure
- Remove all emoji characters
- Include code examples where appropriate
- Maintain table of contents for longer documents

### 4. Validate Changes

Before committing:

```bash
# Validate YAML syntax
yamllint .

# Validate JSON schemas
jsonschema -i schema/agent-schema.json agents/*.yaml

# Check file counts and structure
find . -maxdepth 1 -type d | sort

# Verify total lines
wc -l {agents,roles,skills,schema,data}/*.{yaml,json}
```

### 5. Commit Changes

```bash
git add .
git commit -m "type: description

Detailed explanation of changes:
- What was changed
- Why it was changed
- Any impacts or considerations"
```

**Commit Types**:

- `feat`: New feature or agent definition
- `fix`: Bug fix or correction
- `docs`: Documentation improvements
- `refactor`: Restructuring without changing functionality
- `perf`: Performance improvements
- `test`: Adding tests or validation

**Example**:

```bash
git commit -m "feat: add tier2-cloud-forensic-agent

Adds new cloud-specific forensic analysis agent:
- Analyzes cloud infrastructure logs
- Integrates with AWS CloudTrail and GCP Audit Logs
- Provides forensic analysis for cloud-native environments
- Integrates with tier3 evidence collection

Closes #25"
```

### 6. Push and Create Pull Request

```bash
git push origin feature/your-feature-name
```

Then create a Pull Request on GitHub with:

- **Title**: Clear, concise description
- **Description**: What was changed and why
- **Related Issues**: Reference any related issues
- **Testing**: How changes were tested
- **Checklist**: Confirm validation steps completed

## Validation Checklist

Before submitting a pull request, ensure:

- [ ] All new agents link to valid roles via role_id
- [ ] All agents use skills that exist in skills-matrix.yaml
- [ ] All new roles link to valid agents
- [ ] All new skills are referenced by at least one agent
- [ ] YAML syntax is valid (no indentation errors)
- [ ] JSON schemas are valid
- [ ] Documentation has no emoji characters
- [ ] File structure follows existing patterns
- [ ] Changes don't break existing components
- [ ] All files are in the appropriate root-level directories

## Naming Conventions

### Agent IDs

- Format: `tier[1-3|<type>]-[function]-[type]`
- Examples: `tier1-alert-parser`, `tier2-malware-analyzer`, `cloud-hunter-infrastructure-analyzer`

### Role IDs

- Format: `t[1-3|<initial>]-[function]`
- Examples: `t1-alert-normalization`, `t2-malware-analysis`, `ch-infrastructure-security`

### Skill IDs

- Format: `skill-[category]-[description]`
- Examples: `skill-core-kusto-query`, `skill-forensic-evidence-collection`

### Workflow IDs

- Format: `workflow-[process]-[type]`
- Examples: `workflow-alert-to-resolution`, `workflow-cloud-hunting`

## Merge Process

1. **Review**: At least one maintainer reviews the PR
2. **Validation**: All checks pass (syntax, schema, structure)
3. **Discussion**: Address any feedback or questions
4. **Approval**: Maintainers approve the changes
5. **Merge**: Changes are merged to main branch
6. **Release**: Changes included in next release/tag

## Questions or Issues?

If you have questions:

1. Review existing documentation: [HIERARCHY_README.md](HIERARCHY_README.md), [INDEX.md](INDEX.md)
2. Check [INDEX.md](INDEX.md) for relevant sections
3. Create a GitHub issue with your question
4. Tag with appropriate labels

## Release Process

- Releases follow semantic versioning (major.minor.patch)
- Releases are tagged in git with version number
- Release notes document changes and improvements in CHANGELOG.md
- Updates to version are made in README, CHANGELOG, and CONTRIBUTING files

## Examples

### Adding a New Agent

1. Open `agents/tier2-agents.yaml` (or appropriate tier)
2. Add new agent entry with all required fields
3. Ensure role_id points to valid role in `roles/roles-matrix.yaml`
4. Verify all skills exist in `skills/skills-matrix.yaml`
5. Commit with message: `feat: add tier2-<agent-name>`

### Adding a New Skill

1. Open `skills/skills-matrix.yaml`
2. Add skill entry with level, category, description
3. Ensure referenced agents exist
4. Commit with message: `feat: add skill-<category>-<name>`

### Updating Workflows

1. Open `data/workflows.yaml`
2. Modify or add workflow steps
3. Update SLA and escalation criteria
4. Test that workflow matches agent capabilities
5. Commit with message: `docs: update workflow-<name>`

## Recognition

Contributors are recognized for:

- Bug reports and fixes
- Feature additions
- Documentation improvements
- Testing and quality assurance
- Community engagement

Thank you for helping improve SentinelMCP!

---

**Last Updated**: February 14, 2026
