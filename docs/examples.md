# Examples

This document provides concrete examples of how these rules work in practice across different types of projects.

## Example 1: Local automation script

### Scenario
A Python script that watches a folder for new PDF files, processes them, and stores results in Airtable.

### How rules apply

**Project playbook** (`00-project-playbook.mdc`):
```
Repo map:
- Key directories: src/, data/, logs/
- Entry points: src/main.py
- Config/env: .env (Airtable API key, watched folder path)
- Data storage(s): Airtable base "Document Processing"

Common commands:
- Install: pip install -r requirements.txt
- Dev: python src/main.py --watch ~/Downloads
- Run a job locally: python src/main.py --process-file path/to/file.pdf
- Logs: logs/processing.log
```

**Local runner rules** (`03-local-runner-and-triggers.mdc`):
- Uses watched folder pattern (iCloud/Dropbox/local)
- Implements file watcher using native OS capabilities
- Provides clear start/stop instructions

**Airtable usage** (`04-airtable-usage.mdc`):
- Uses Airtable for shared, queryable results
- Documents base ID and table structure
- Includes error handling for API failures

**Safety rules** (`06-safety-reversibility.mdc`):
- Stores API key in `.env` file (never committed)
- Keeps original PDFs, writes outputs separately
- Implements dry-run mode for testing

### Example playbook entry

```markdown
Session log:
- 2025-01-15: Set up folder watcher, integrated Airtable API. Next: Add error recovery for network failures.
- 2025-01-16: Added retry logic and better error messages. Next: Test with iPhone Share Sheet integration.
```

## Example 2: Web application with Tailscale endpoint

### Scenario
A Flask web app that receives data from iPhone Shortcuts via Tailscale, processes it, and returns results.

### How rules apply

**Project playbook**:
```
Repo map:
- Key directories: app/, templates/, static/
- Entry points: app/main.py (Flask app)
- Config/env: .env (API keys, Tailscale hostname)
- Data storage(s): SQLite database (app/data.db)

Common commands:
- Install: pip install -r requirements.txt
- Dev: flask run --host 0.0.0.0 --port 5000
- Logs: logs/app.log (view with: tail -f logs/app.log)
- Run a job locally: python -m app.processor --input data.json
```

**Tailscale patterns** (`12-tailscale-patterns.mdc`):
- Documents Tailscale hostname and port
- Explains iPhone Shortcut configuration
- Includes failure recovery steps

**UI/UX rules** (`09-ui-ux.mdc`):
- Provides clear error messages
- Includes loading states
- Accessible form inputs

**Verification rules** (`07-verification-handover.mdc`):
- Runbook includes: how to start service, how to test endpoint, where logs are
- Manual verification: "Send test data from iPhone, check logs for success message"

### Example Tailscale endpoint documentation

See `docs/tailscale-endpoint-pattern.md` for the template. Filled example:

```markdown
## Endpoint
- Base url: `http://macstudio.tailnet-abc123.ts.net:5000`
- Path(s):
  - `POST /api/process`
- Auth:
  - Header name: `X-API-Key`
  - How the secret is stored: In iPhone Shortcut (stored securely)

## iPhone shortcut
- Shortcut name: "Process Document"
- Trigger: Share Sheet
- What it sends: Selected file + metadata
- What user sees as confirmation: "Processing... Check app for results"
```

## Example 3: LLM-powered document analysis

### Scenario
A script that uses OpenAI API to analyse medical documents and extract structured information.

### How rules apply

**LLM integration** (`05-llm-integration.mdc`):
- Documents API provider and model selection
- Includes prompt engineering patterns
- Handles rate limiting and retries

**Safety rules** (`06-safety-reversibility.mdc`):
- Never prints full API keys in logs
- Redacts sensitive identifiers in examples
- Keeps original documents, writes analysis separately

**Collaboration style** (`01-collaboration-style.mdc`):
- Treats user as domain expert (medical professional)
- Makes technical decisions autonomously
- Only asks about medical/domain-specific choices

**Project playbook**:
```
Operational notes:
- Where logs go: logs/analysis.log
- Where outputs go: outputs/structured/ (JSON files)
- How to start/stop: Run as one-off script, no background service
- Backups: Original documents kept in inputs/archive/

Session log:
- 2025-01-15: Implemented basic extraction. Next: Add validation for medical terminology.
- 2025-01-16: Added terminology validation. Next: Test with real case files.
```

## Example 4: GitHub Actions automation

### Scenario
A GitHub Actions workflow that processes data on a schedule and updates a repository.

### How rules apply

**Git and GitHub Actions** (`08-git-and-github-actions.mdc`):
- Documents workflow triggers and schedule
- Explains how secrets are stored in GitHub
- Includes rollback procedures

**Safety rules**:
- Uses GitHub Secrets for API keys
- Implements dry-run mode for testing
- Keeps audit trail of changes

**Verification rules**:
- Runbook includes: how to trigger manually, how to check logs, how to verify outputs
- Provides commands: `gh workflow run process-data.yml`

## Example 5: Greenfield web application

### Scenario
Building a new React + Node.js application from scratch.

### How rules apply

**Greenfield builds** (`13-greenfield-builds.mdc`):
- Sets up modern, beautiful UI
- Follows best UX practices
- Includes accessibility basics

**UI/UX rules** (`09-ui-ux.mdc`):
- Consistent design system
- Accessible components
- Testable behaviours

**Testing rules** (`11-testing-quality-gates.mdc`):
- Unit tests for core logic
- Integration tests for API
- E2E tests for critical flows

**Project playbook**:
```
Common commands:
- Install: npm install (both frontend/ and backend/)
- Dev: npm run dev (starts both frontend and backend)
- Build: npm run build
- Test: npm test
- Lint: npm run lint
- Typecheck: npm run typecheck

Repo map:
- Key directories: frontend/, backend/, shared/
- Entry points: frontend/src/index.tsx, backend/src/server.ts
- Config/env: frontend/.env, backend/.env
- Data storage(s): PostgreSQL database
```

## Common patterns

### Pattern: Environment setup

Every project should have:
- `.env.example` with all required variables documented
- `.gitignore` that excludes `.env` files
- Code that loads env vars at startup and fails fast if missing
- Documentation of where secrets are stored

### Pattern: Logging

Consistent logging approach:
- Logs go to `logs/` directory (gitignored)
- Use structured logging when possible
- Include timestamps and context
- Never log secrets or sensitive data

### Pattern: Error handling

- Fail fast with clear error messages
- Provide actionable error output
- Include recovery steps in runbooks
- Log errors with sufficient context

### Pattern: Documentation

- README with: install, run, deploy instructions
- Runbook with: troubleshooting, common failures, recovery steps
- Playbook with: project memory, commands, operational notes
- Code comments for non-obvious logic

## Learning from examples

When starting a new project:

1. Find a similar example above
2. Copy the relevant playbook structure
3. Adapt the commands and paths to your project
4. Reference the applicable rule files
5. Update the playbook as you learn project-specific details

These examples should evolve as we learn what works well in practice. Consider contributing new examples or improvements back to this template repository.
