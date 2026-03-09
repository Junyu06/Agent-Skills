---
name: ai-vault-sync
description: Use this skill to load, use, and synchronize a shared AI memory vault for a specific repository or project. Trigger it when the user points to a central vault such as an ai-playbook or Obsidian-style notes repo, asks to reuse persistent cross-repo context, wants the agent to read a project file first, or wants durable changes written back into project, decision, architecture, pattern, or log notes with minimal scanning.
---

# AI Vault Sync

## Overview

Treat the vault as persistent project context, not as something to crawl broadly. Read the smallest useful slice, use it to guide the current task, and write back only durable changes.

## Workflow

1. Identify the vault path and current project.
2. Read the vault rules file first if one is present.
3. Read the matching project file under `projects/` before any broader vault scan.
4. Read only the additional notes needed for the task.
5. Reconcile the vault with durable changes from the current conversation or repository work.
6. Update only the files whose durable context actually changed.

## Read Order

Use this order unless the user explicitly overrides it:

1. Vault usage rules such as `AGENT_RULES.md` or equivalent.
2. `projects/<project>.md` for the active repo or initiative.
3. Only the minimum extra files needed from:
   - `architecture/`
   - `decisions/`
   - `patterns/`
   - `logs/`

Do not scan the entire vault by default.

## Project File Expectations

Treat the project file as the primary persistent context. Expect it to summarize:

- Goal
- Tech stack
- Current phase
- Key modules
- Constraints
- Next steps

If the vault uses a different but obviously equivalent structure, adapt without forcing a rewrite unless the user asks.

## Write Rules

Update the vault only when the current work changed durable context. Durable changes usually include:

- Project phase changed.
- Architecture changed.
- Important constraints changed.
- Next steps changed materially.
- A major technical decision was made.
- Recent work changed the lasting project state enough to merit a log entry.

Use these destinations:

- Update `projects/<project>.md` for project summary changes.
- Write repo-specific decisions under `decisions/<project>/`.
- Write cross-project or vault-level decisions under `decisions/shared/`.
- Add or update logs under `logs/` when recent work changed durable state.
- Update `architecture/` or `patterns/` only when those documents are actually affected.

## Reconciliation Rule

When the user says work has already happened in the current chat, reconcile the vault against:

1. The current conversation.
2. The repository state relevant to the task.
3. Existing vault notes already loaded for this task.

Do not rewrite notes just to restate transient implementation detail. Prefer compact updates that preserve the vault as high-signal memory.

## Missing Information

If the vault path is known but the project is unclear, infer it from the repo name or current task when that is reliable. Ask one concise question only when the project cannot be inferred safely.

If the vault does not yet contain a project file, create one only if the user asked to initialize or extend the vault; otherwise continue with the task and note the gap.

## Output Discipline

When closing the task, mention whether the vault was synchronized, which files were touched, and any durable context that still needs confirmation.
