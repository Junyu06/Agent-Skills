# Agent Skills

Backup library for reusable AI agent skills copied from active Codex global skills or created locally for cross-agent reuse.

## Purpose
- Keep a portable copy of important skills outside agent-specific hidden directories
- Make it easy to inspect, version, and copy skills into other agent environments
- Preserve both the core `SKILL.md` instructions and any agent metadata such as `agents/openai.yaml`

## Current Skills
- `ai-vault-sync`: Load a shared AI memory vault, read the relevant project file first, and synchronize durable context updates back into the vault
- `summary-context-only`: Summarize only the current conversation context into a dense handoff without external tools
- `repo-flow-demo`: Build an interactive repository architecture walkthrough with Mermaid diagrams and repo-specific visual storytelling

## Structure
- One folder per skill
- Each skill should keep its original folder name
- Preserve `SKILL.md` and any required subfolders such as `agents/`, `scripts/`, `references/`, or `assets/`

## Maintenance Rules
- When a global Codex skill is added or materially updated, copy the latest version here
- Keep this directory focused on reusable skills, not one-off prompts or scratch notes
- If a skill is adapted for another agent, prefer adding wrapper files without overwriting the original Codex skill contents
