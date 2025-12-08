# Usage guide

## Overview

This repository provides a standardised set of rules and playbooks for AI-assisted development projects. These rules ensure consistency, quality, and maintainability across multiple projects and development sessions.

## How to use this template

### For new projects

1. **Copy or reference these rules** in your new project repository
   - Option A: Copy the `.cursor/rules/` directory to your project
   - Option B: Reference this repository in your Cursor IDE configuration
   - Option C: Use this repository as a template when creating new projects

2. **Initialise the project playbook**
   - Open `.cursor/rules/00-project-playbook.mdc`
   - Fill in the repo map with your project structure
   - Document common commands (install, dev, test, etc.)
   - Add operational notes (logs, outputs, backups)

3. **Customise rules as needed**
   - Review each rule file to understand what it covers
   - Modify or extend rules for project-specific needs
   - Add new rule files for domain-specific patterns

### For existing projects

1. **Review current practices**
   - Identify gaps in your current development workflow
   - Determine which rules would benefit your project

2. **Gradually adopt rules**
   - Start with the project playbook (00-project-playbook.mdc)
   - Add collaboration style rules (01-collaboration-style.mdc)
   - Introduce other rules as relevant to your project type

3. **Update the playbook**
   - Document your existing project structure
   - Add your common commands and workflows
   - Note any project-specific conventions

## Rule files explained

### Core rules (always applied)

- **00-project-playbook.mdc** - Project memory and defaults. The AI maintains this file with project-specific information.
- **01-collaboration-style.mdc** - How the AI should interact with you (domain expert vs co-developer).
- **02-explore-plan-implement.mdc** - The default development loop: explore → plan → implement → verify → summarise.
- **06-safety-reversibility.mdc** - Privacy, secrets handling, and reversible design principles.
- **07-verification-handover.mdc** - Definition of done and runbook requirements.

### Optional rules (requestable)

- **03-local-runner-and-triggers.mdc** - Patterns for local automation (watched folders, droplets, etc.).
- **04-airtable-usage.mdc** - Guidelines for when and how to use Airtable.
- **05-llm-integration.mdc** - Patterns for integrating LLM APIs.
- **08-git-and-github-actions.mdc** - Git workflow and GitHub Actions patterns.
- **09-ui-ux.mdc** - UI/UX consistency and accessibility guidelines.
- **10-checklists-scratchpads.mdc** - Patterns for managing checklists and scratchpads.
- **11-testing-quality-gates.mdc** - Testing standards and quality gates.
- **12-tailscale-patterns.mdc** - Patterns for Tailscale endpoints (see `docs/tailscale-endpoint-pattern.md`).
- **13-greenfield-builds.mdc** - Patterns for building new applications from scratch.

## Workflow integration

### Development session flow

1. **Start of session**
   - AI reads the playbook to understand project state
   - Checks git log for recent changes
   - Identifies the next logical task

2. **During development**
   - Follows explore → plan → implement → verify → summarise loop
   - Updates playbook as new information is learned
   - Maintains backwards compatibility

3. **End of session**
   - Commits progress with clear messages
   - Updates playbook session log
   - Ensures codebase is in a clean, mergeable state

### Multi-session continuity

The playbook serves as project memory between sessions:
- Recent commits and their context
- Current project state and next steps
- Operational notes (where logs go, how to run, etc.)
- Known issues or blockers

## Customisation tips

### Adding project-specific rules

Create new `.mdc` files in `.cursor/rules/` following the existing pattern:
- Use descriptive filenames (e.g., `14-database-patterns.mdc`)
- Include a description header
- Specify glob patterns if the rule applies to specific file types
- Set `alwaysApply: true` if the rule should always be active

### Modifying existing rules

- Rules are markdown files, so they're easy to edit
- Keep changes focused and well-documented
- Test rule changes in a small project first
- Consider backwards compatibility with existing projects

### Environment-specific notes

- Document Mac Studio-specific paths or commands
- Note any Tailscale or network requirements
- Include iPhone/iCloud integration patterns if relevant
- Document Airtable base IDs or API keys (securely)

## Best practices

1. **Keep the playbook updated**
   - Update it whenever you learn something new about the project
   - Document commands, conventions, and "gotchas"
   - Keep the session log concise but informative

2. **Use appropriate rules**
   - Don't enable all rules for every project
   - Choose rules that match your project type (web app, automation, CLI tool, etc.)
   - Disable or modify rules that don't fit your workflow

3. **Maintain consistency**
   - Follow the same patterns across projects when possible
   - Document deviations and their reasons
   - Share learnings back to this template repository

4. **Security first**
   - Never commit secrets or `.env` files
   - Use `.env.example` files with placeholders
   - Document where secrets are stored and how they're loaded

## Troubleshooting

### Rules not being applied

- Check that `.cursor/rules/` files are in the correct location
- Verify Cursor IDE is configured to use these rules
- Ensure rule files have valid frontmatter headers

### Playbook not updating

- The AI should update the playbook automatically
- If it's not happening, explicitly ask the AI to update it
- Check that the playbook file is writable

### Conflicting rules

- Review rule files for overlapping guidance
- More specific rules should take precedence
- Consider consolidating or clarifying conflicting rules

## Getting help

- Review the examples in `docs/examples.md`
- Check the quick-start checklist in `docs/quick-start.md`
- Refer to specific rule files for detailed guidance
- Consult the Tailscale endpoint pattern template if building endpoints
