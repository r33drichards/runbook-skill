# Runbook Skill

A Claude skill for creating, reviewing, and improving operational runbooks.

## Installation

### Claude Code

Add to your `.claude/settings.json`:

```json
{
  "permissions": {
    "additionalDirectories": [
      "/path/to/runbook-skill"
    ]
  }
}
```

Or clone and reference in your project's `.mcp.json` or skill configuration.

### Claude.ai

Upload the `runbook.skill` file from [Releases](../../releases) to your Claude.ai workspace.

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
