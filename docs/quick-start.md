# Quick start checklist

Use this checklist when starting a new project with these rules.

## Initial setup

### 1. Repository setup
- [ ] Create new repository or copy this template
- [ ] Copy `.cursor/rules/` directory to your project
- [ ] Ensure `.gitignore` includes `.env`, `logs/`, `tmp/`, etc.
- [ ] Create `README.md` with project description

### 2. Project playbook initialisation
- [ ] Open `.cursor/rules/00-project-playbook.mdc`
- [ ] Fill in **Repo map**:
  - [ ] Key directories
  - [ ] Entry points (main files, scripts)
  - [ ] Config/env file locations
  - [ ] Data storage locations
- [ ] Fill in **Common commands**:
  - [ ] Install dependencies
  - [ ] Development mode
  - [ ] Build (if applicable)
  - [ ] Test
  - [ ] Lint/format/typecheck
  - [ ] Run a job locally
  - [ ] Deploy/release (if applicable)
- [ ] Fill in **Operational notes**:
  - [ ] Where logs go
  - [ ] Where outputs go
  - [ ] How to start/stop background jobs
  - [ ] Backup procedures

### 3. Environment configuration
- [ ] Create `.env.example` with all required variables
- [ ] Document each variable with comments
- [ ] Create `.env` locally (never commit this)
- [ ] Verify `.gitignore` excludes `.env` files
- [ ] Test that code fails fast if required env vars are missing

### 4. Rule selection
Review and enable relevant rules:
- [ ] **Always applied** (already active):
  - [x] Project playbook
  - [x] Collaboration style
  - [x] Explore-plan-implement
  - [x] Safety and reversibility
  - [x] Verification and handover
- [ ] **Optional rules** (enable if relevant):
  - [ ] Local runner and triggers (for automation scripts)
  - [ ] Airtable usage (if using Airtable)
  - [ ] LLM integration (if using LLM APIs)
  - [ ] Git and GitHub Actions (if using GitHub workflows)
  - [ ] UI/UX (for web/frontend projects)
  - [ ] Checklists and scratchpads (if managing complex workflows)
  - [ ] Testing and quality gates (for projects with tests)
  - [ ] Tailscale patterns (if building Tailscale endpoints)
  - [ ] Greenfield builds (for new applications)

## First development session

### 5. Project structure
- [ ] Create basic directory structure
- [ ] Set up entry point(s)
- [ ] Add initial dependencies (requirements.txt, package.json, etc.)
- [ ] Create basic configuration files

### 6. Initial implementation
- [ ] Implement minimal working version
- [ ] Add error handling
- [ ] Set up logging
- [ ] Test locally

### 7. Documentation
- [ ] Update README with:
  - [ ] What the project does
  - [ ] How to install prerequisites
  - [ ] How to run once
  - [ ] How to run continuously (if applicable)
  - [ ] Where outputs go
  - [ ] Where logs go
  - [ ] How to troubleshoot common failures
- [ ] Update playbook session log with initial setup notes

## Ongoing development

### 8. Each session start
- [ ] Read playbook to understand current state
- [ ] Check git log for recent commits
- [ ] Run dev/test command to verify environment works
- [ ] Identify next logical task

### 9. During development
- [ ] Follow explore → plan → implement → verify → summarise loop
- [ ] Update playbook when learning new commands or conventions
- [ ] Keep changes small and focused
- [ ] Maintain backwards compatibility where possible

### 10. End of session
- [ ] Commit progress with clear, descriptive message
- [ ] Update playbook session log:
  - [ ] What was done
  - [ ] What's next
  - [ ] Any blockers or decisions
- [ ] Ensure codebase is in clean, mergeable state
- [ ] Verify all tests pass (if applicable)

## Project-specific additions

### For automation scripts
- [ ] Document trigger mechanism (watched folder, cron, etc.)
- [ ] Add dry-run mode
- [ ] Include recovery procedures
- [ ] Test failure scenarios

### For web applications
- [ ] Set up development server
- [ ] Configure production deployment
- [ ] Add health check endpoint
- [ ] Document API endpoints (if applicable)

### For Tailscale endpoints
- [ ] Fill in `docs/tailscale-endpoint-pattern.md` template
- [ ] Document Tailscale hostname and port
- [ ] Create iPhone Shortcut (if applicable)
- [ ] Test endpoint accessibility
- [ ] Document failure recovery

### For LLM integrations
- [ ] Document API provider and model
- [ ] Set up rate limiting
- [ ] Implement retry logic
- [ ] Add prompt versioning (if applicable)

### For Airtable integrations
- [ ] Document base ID and table structure
- [ ] Create `.env.example` with base ID
- [ ] Test read/write operations
- [ ] Document error handling

## Verification

### 11. Before considering complete
- [ ] Feature runs end-to-end on realistic inputs
- [ ] Failures are visible and actionable (not silent)
- [ ] User has simple run/stop instructions
- [ ] Runbook includes troubleshooting for top 3 likely failures
- [ ] Manual verification checklist exists (if UI component)
- [ ] All secrets stored securely (never committed)
- [ ] `.env.example` is complete and accurate

## Handover

### 12. For project handover
- [ ] README is complete and up-to-date
- [ ] Playbook contains all operational knowledge
- [ ] Runbook exists with troubleshooting steps
- [ ] All commands documented and tested
- [ ] Environment setup is reproducible
- [ ] Known issues documented
- [ ] Next steps clearly identified

## Tips

- **Start small**: Don't try to fill everything in at once. The playbook grows organically.
- **Update as you go**: When you learn something new (a command, a gotcha, a convention), update the playbook immediately.
- **Be specific**: Instead of "run the script", document the exact command: `python src/main.py --input data.json`
- **Include context**: Note why something is done a certain way, not just how.
- **Keep it concise**: The playbook is project memory, not full documentation. Keep entries short and focused.

## Getting help

- Review `docs/usage-guide.md` for detailed explanations
- Check `docs/examples.md` for concrete examples
- Refer to specific rule files in `.cursor/rules/` for domain-specific guidance
- Consult `docs/tailscale-endpoint-pattern.md` if building endpoints
