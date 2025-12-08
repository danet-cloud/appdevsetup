# Development project rules

Starting point for new AI development projects.

This repository contains project rules and playbooks for AI-assisted development work. These rules guide the AI assistant in maintaining consistency, following best practices, and ensuring quality across development projects.

## Quick start

1. **New to this template?** Start with the [Quick start checklist](docs/quick-start.md)
2. **Want to understand how it works?** Read the [Usage guide](docs/usage-guide.md)
3. **Need examples?** See [Examples](docs/examples.md) for concrete project scenarios
4. **Building a Tailscale endpoint?** Use the [Tailscale endpoint pattern](docs/tailscale-endpoint-pattern.md) template

## Structure

- `.cursor/rules/` - Cursor IDE rules for AI collaboration
  - Project playbook and collaboration guidelines
  - Patterns for local-first automation, Airtable integration, LLM usage
  - Safety, testing, and verification standards
  - UI/UX guidelines and greenfield build patterns
- `docs/` - Additional documentation and patterns
  - `usage-guide.md` - Comprehensive guide on using these rules
  - `examples.md` - Concrete examples across different project types
  - `quick-start.md` - Step-by-step checklist for new projects
  - `tailscale-endpoint-pattern.md` - Template for Tailscale endpoints

## Purpose

These rules ensure:
- Consistent development practices across projects
- Local-first automation preferences
- Proper handling of sensitive data and secrets
- Quality gates and testing standards
- Clear verification and handover processes
- Project memory that persists across multiple development sessions

## How to use

### Option 1: Copy rules to your project
Copy the `.cursor/rules/` directory to your project repository. The rules will be automatically applied by Cursor IDE.

### Option 2: Reference as template
Use this repository as a template when creating new projects. GitHub allows you to create a repository from a template.

### Option 3: Configure in workspace
Reference this repository in your Cursor IDE workspace configuration to apply rules across multiple projects.

## Getting started

1. **Initialise your project playbook**
   - Open `.cursor/rules/00-project-playbook.mdc`
   - Fill in your repo map, common commands, and operational notes
   - See the [Quick start checklist](docs/quick-start.md) for details

2. **Select relevant rules**
   - Core rules are always applied
   - Enable optional rules based on your project type (see [Usage guide](docs/usage-guide.md))

3. **Start developing**
   - The AI will read your playbook at the start of each session
   - Follow the explore → plan → implement → verify → summarise loop
   - Update the playbook as you learn project-specific details

## Documentation

- **[Usage guide](docs/usage-guide.md)** - Comprehensive explanation of how to use these rules, customisation tips, and troubleshooting
- **[Examples](docs/examples.md)** - Real-world examples showing how rules apply to different project types
- **[Quick start](docs/quick-start.md)** - Step-by-step checklist for setting up a new project
- **[Tailscale endpoint pattern](docs/tailscale-endpoint-pattern.md)** - Template for documenting Tailscale endpoints

## Rule files overview

### Core rules (always applied)
- `00-project-playbook.mdc` - Project memory and defaults
- `01-collaboration-style.mdc` - AI collaboration approach
- `02-explore-plan-implement.mdc` - Development workflow
- `06-safety-reversibility.mdc` - Security and data handling
- `07-verification-handover.mdc` - Quality and documentation standards

### Optional rules (enable as needed)
- `03-local-runner-and-triggers.mdc` - Local automation patterns
- `04-airtable-usage.mdc` - Airtable integration guidelines
- `05-llm-integration.mdc` - LLM API patterns
- `08-git-and-github-actions.mdc` - Git and CI/CD workflows
- `09-ui-ux.mdc` - UI/UX consistency and accessibility
- `10-checklists-scratchpads.mdc` - Workflow management patterns
- `11-testing-quality-gates.mdc` - Testing standards
- `12-tailscale-patterns.mdc` - Tailscale endpoint patterns
- `13-greenfield-builds.mdc` - New application build patterns

See the [Usage guide](docs/usage-guide.md) for detailed explanations of each rule file.

## Inspiration

These rules are based on Anthropic's research on [Effective harnesses for long-running agents](https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents) (26 November 2025), which outlines best practices for enabling AI agents to make consistent progress across multiple context windows.
