# Support Documentation

Help, troubleshooting, and support materials for SentinelMCP operations.

## Overview

This directory contains troubleshooting guides, performance tuning, and support resources for operational issues.

## Quick Navigation

### Help & Support

- [Troubleshooting Guide](TROUBLESHOOTING.md) - Common issues and fixes
- [FAQ](../FAQ.md) - Frequently asked questions
- [Known Issues](KNOWN_ISSUES.md) - Issues we're tracking

### Performance & Tuning

- [Performance Tuning](PERFORMANCE_TUNING.md) - Optimization guide
- [Capacity Planning](CAPACITY_PLANNING.md) - Scaling your system
- [Cost Estimation](COST_ESTIMATION.md) - Budget planning

### Compatibility & Versioning

- [Version Compatibility](VERSION_COMPATIBILITY.md) - Version support matrix
- [Migration Guide](MIGRATION_GUIDE.md) - Upgrading between versions
- [Deprecation Notice](DEPRECATION_NOTICE.md) - Features being removed

## Files in This Directory

| File                       | Purpose                 | Use When                  |
| -------------------------- | ----------------------- | ------------------------- |
| `TROUBLESHOOTING.md`       | Common issues and fixes | Something is broken       |
| `KNOWN_ISSUES.md`          | Documented problems     | You think you found a bug |
| `PERFORMANCE_TUNING.md`    | Optimization guide      | System is slow            |
| `CAPACITY_PLANNING.md`     | Scaling guidance        | Planning growth           |
| `COST_ESTIMATION.md`       | Budget calculator       | Estimating costs          |
| `VERSION_COMPATIBILITY.md` | Version support         | Checking compatibility    |
| `MIGRATION_GUIDE.md`       | Upgrade procedures      | Upgrading versions        |
| `DEPRECATION_NOTICE.md`    | Features being removed  | Planning for changes      |

## Getting Help

### 1. Check the Obvious

- Verify configuration: `cat config.yaml`
- Check workspace ID matches: `grep workspace_id config.yaml`
- Verify workspace is accessible: Log into Sentinel portal

### 2. Check Troubleshooting Guide

→ [TROUBLESHOOTING.md](TROUBLESHOOTING.md)

- 90% of issues covered here
- Quick fixes and diagnostics

### 3. Check Known Issues

→ [KNOWN_ISSUES.md](KNOWN_ISSUES.md)

- Issues we already know about
- Workarounds if available
- ETA on fixes

### 4. Check FAQ

→ [FAQ](../FAQ.md)

- General questions
- Best practices
- Tips and tricks

### 5. Diagnostic Steps

If you've checked the above:

1. **Collect information**:
   - Your version: Check [VERSION_COMPATIBILITY.md](VERSION_COMPATIBILITY.md)
   - Your configuration (masked)
   - Error messages or logs
   - Steps to reproduce

2. **Check logs**:
   - Sentinel workspace logs
   - Azure Activity Log
   - Azure Monitor diagnostics

3. **Create an issue**:
   - GitHub: [github.com/eshlomo1/SentinelMCP/issues](https://github.com/eshlomo1/SentinelMCP/issues)
   - Include diagnostic info from step 1
   - Include error messages and logs
   - Describe what you expected vs. what happened

## Common Issue Categories

### Configuration Issues

- Missing workspace ID
- Wrong region/tenant
- Firewall/network blocks
- Data source not connected

→ Check: [TROUBLESHOOTING.md](TROUBLESHOOTING.md) - Configuration section

### Performance Issues

- Slow alert processing
- Delayed escalations
- Query timeouts
- High resource usage

→ Check: [PERFORMANCE_TUNING.md](PERFORMANCE_TUNING.md)

### Escalation Issues

- Alerts not escalating
- Wrong tier escalation
- SLA timeouts
- Authority conflicts

→ Check: [Tier Integration](../OPERATIONS/TIER_INTEGRATION.md)

### Data Issues

- Missing evidence
- Schema validation errors
- Data not flowing
- Forensic gaps

→ Check: [TROUBLESHOOTING.md](TROUBLESHOOTING.md) - Data section

## Support Levels

### Free Support

- Documentation review
- FAQ lookup
- Known issues search
- Community GitHub issues

### Professional Support

Contact: PurpleX Lab Security Operations

- Consultation
- Customization assistance
- Training
- On-site support

## Version Support Policy

### Current Version

**v1.0.2** (February 2026)

- Full support
- Regular updates
- Security patches

### Previous Versions

**v1.0.1** - Security patches only  
**v1.0.0** - Limited support (consider upgrading)

See [VERSION_COMPATIBILITY.md](VERSION_COMPATIBILITY.md) for full support matrix.

## Reporting Issues

### For Bugs

1. Check [KNOWN_ISSUES.md](KNOWN_ISSUES.md) first
2. Gather information (version, config, logs)
3. Provide steps to reproduce
4. Submit on GitHub

### For Features

1. Check [Roadmap](../ARCHITECTURE/ROADMAP.md) for planned features
2. Describe desired behavior
3. Explain use case
4. Submit GitHub discussion

### For Security Issues

⚠️ **DO NOT post security issues publicly**

- Email: security@purplexlab.com
- Include severity assessment
- Allow time for remediation

## Performance Benchmarks

| Metric              | Expected | Slow     | Needs Tuning |
| ------------------- | -------- | -------- | ------------ |
| Tier 1 Processing   | < 5 sec  | > 30 sec | > 1 min      |
| Escalation Decision | < 2 sec  | > 10 sec | > 30 sec     |
| Tier 2 Analysis     | < 2 min  | > 5 min  | > 10 min     |
| Query Response      | < 30 sec | > 2 min  | > 5 min      |

See [PERFORMANCE_TUNING.md](PERFORMANCE_TUNING.md) if exceeding slow times.

## Maintenance Windows

No scheduled maintenance required. System designed for continuous operation.

However, consider:

- Monthly documentation reviews
- Quarterly SLA adjustments
- Annual architecture review
- Continuous monitoring

## Support Contacts

| Issue              | Contact                 | Response Time     |
| ------------------ | ----------------------- | ----------------- |
| Documentation      | GitHub Issues           | 2-5 business days |
| Bug Report         | GitHub Issues           | 1-3 business days |
| Feature Request    | GitHub Discussion       | 1-2 weeks         |
| Security Issue     | security@purplexlab.com | 24 hours          |
| Operations Support | SOC Manager             | Immediate         |

## Resources

- **Documentation**: [DOCS/](../) directory
- **Code Repository**: [github.com/eshlomo1/SentinelMCP](https://github.com/eshlomo1/SentinelMCP)
- **Issues**: [GitHub Issues](https://github.com/eshlomo1/SentinelMCP/issues)
- **Discussions**: [GitHub Discussions](https://github.com/eshlomo1/SentinelMCP/discussions)

---

**Last Updated**: February 14, 2026 | **Version**: 1.0.2
