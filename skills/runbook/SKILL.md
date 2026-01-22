---
name: runbook
description: |
  Create, review, and improve operational runbooks that enable consistent responses to well-understood events. Use this skill when: (1) Creating new runbooks for operational procedures, (2) Reviewing or improving existing runbooks, (3) Converting ad-hoc procedures into documented runbooks, (4) Building incident response documentation, or (5) When users mention "runbook", "playbook", "operational procedure", or "incident response documentation".
---

# Runbook Skill

Create runbooks that enable adequately skilled team members to successfully complete procedures, even without prior familiarity.

## Core Principles

1. **Minimum viable documentation** - Include only what's necessary for successful execution
2. **Start manual, then automate** - Valid manual process first, then codify
3. **Reversibility** - Every runbook must have a rollback path
4. **Verifiability** - Include success criteria for each step

## Runbook Structure

Use this structure for all runbooks:

```markdown
# [Procedure Name]

## Overview
One-sentence description of what this runbook accomplishes.

## Requirements
- **Permissions**: [Required access/roles]
- **Tools**: [Required software/configurations]
- **Network**: [Required connectivity/access]

## Constraints
- **Maintenance windows**: [When this can run]
- **Impacted resources**: [What gets affected]
- **Conflicts**: [Other activities that conflict]

## Procedure

### Step 1: [Action]
**Action**: [What to do]
**Expected outcome**: [What success looks like]
**If failed**: [What to do if this step fails]

### Step 2: [Action]
...

## Verification
How to confirm the runbook achieved its intended outcome.

## Rollback
Steps to revert changes if needed.

## Escalation
- **Escalate to**: [Person/team]
- **Escalate after**: [Time threshold]
- **Decision makers**: [Who to contact before execution, if any]
- **Third-party support**: [Contact info, contract details if applicable]
```

## Prioritization Guidance

When helping users decide which runbooks to create first:
1. **High frequency** - Procedures run often (reduces operational burden)
2. **High error rate** - Procedures prone to mistakes (reduces incidents)
3. **High impact** - Procedures with significant business risk (manages risk)

## Best Practices

- Tag environments explicitly and verify targets via metadata before execution
- Test runbooks with same rigor as application code
- Have new team members follow and document procedures (training + knowledge capture)
- Ensure authentication/authorization controls on runbook execution

## Example

See [references/example_runbook.md](references/example_runbook.md) for a complete example demonstrating this structure.
