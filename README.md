# Development project rules

Starting point for new AI development projects.

This repository contains project rules and playbooks for AI-assisted development work. These rules guide the AI assistant in maintaining consistency, following best practices, and ensuring quality across development projects.

## Structure

- `.cursor/rules/` - Cursor IDE rules for AI collaboration
  - Project playbook and collaboration guidelines
  - Patterns for local-first automation, Airtable integration, LLM usage
  - Safety, testing, and verification standards
  - UI/UX guidelines and greenfield build patterns
- `docs/` - Additional documentation and patterns

## Purpose

These rules ensure:
- Consistent development practices across projects
- Local-first automation preferences
- Proper handling of sensitive data and secrets
- Quality gates and testing standards
- Clear verification and handover processes

## Usage

These rules are automatically applied by Cursor IDE when working in projects that reference this repository or when these rules are configured in the workspace.

## Inspiration

These rules are based on Anthropic's research on [Effective harnesses for long-running agents](https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents) (26 November 2025), which outlines best practices for enabling AI agents to make consistent progress across multiple context windows.
