# Runbook Skill

A Claude skill for creating, reviewing, and improving operational runbooks.

## Installation

### Personal Skills (available in all projects)

```bash
git clone https://github.com/r33drichards/runbook-skill ~/.claude/skills/runbook
```

### Project Skills (single project only)

```bash
git clone https://github.com/r33drichards/runbook-skill .claude/skills/runbook
```

After installation, the skill is available as `/runbook`.

## What This Skill Does

- Creates standardized runbooks for operational procedures
- Reviews and improves existing runbooks
- Converts ad-hoc procedures into documented runbooks
- Builds incident response documentation

## Runbook Structure

The skill enforces a consistent structure:

- **Overview** - One-sentence description
- **Requirements** - Permissions, tools, network access
- **Constraints** - Maintenance windows, impacted resources, conflicts
- **Procedure** - Steps with actions, expected outcomes, and failure handling
- **Verification** - Success criteria
- **Rollback** - Reversion steps
- **Escalation** - Contacts and thresholds

## License

MIT
