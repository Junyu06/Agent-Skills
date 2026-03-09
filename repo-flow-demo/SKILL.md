---
name: repo-flow-demo
description: Create bespoke interactive HTML architecture walkthroughs for any repository, with Mermaid flow diagrams, animated explanation, and repo-specific visual storytelling. Use when asked to explain a codebase visually, build an interactive repo demo, document pipeline flow, generate an architecture page, or turn source code structure into a browsable animated walkthrough.
---

# Repo Flow Demo

Inspect the repository first, then build a custom demo page from scratch for that codebase. Reuse the workflow, not the previous HTML.

## Workflow

1. Read the repository surface area before designing anything.
   Use fast file discovery first.
   Prefer `rg --files`, `rg`, README files, main entrypoints, pipeline modules, and UI/server boot files.

2. Identify the canonical user-facing flow.
   Extract the actual sequence from code, not from guesses.
   Look for:
   - primary entrypoints
   - optional branches
   - background processing steps
   - output/rendering steps
   - platform-specific differences only if they materially change the story

3. Choose the smallest set of steps that explains the system clearly.
   Usually 5-9 steps is enough.
   Each step should map to a real file or function and explain one transition in the system.

4. Build a bespoke single-page demo in HTML.
   Default to a standalone page under `docs/` unless the repository already has a better destination.
   Use plain HTML/CSS/JS unless the repo already has an established frontend stack for docs or demos.

5. Generate a Mermaid flowchart from the discovered flow.
   Make the Mermaid graph reflect the real architecture.
   If the page has toggles or modes, let the Mermaid source react to those controls when that improves clarity.

6. Make the page interactive.
   The minimum interaction set is:
   - clickable step list or timeline
   - synced detail panel
   - Mermaid graph that updates or highlights with the current state
   - responsive layout that works on desktop and mobile

7. Verify the page against the repository.
   Check that every named step is grounded in actual code paths.
   Remove decorative features that are not earning their keep.

## Adaptation Rules

- Do not copy a previous project's HTML wholesale unless the user explicitly asks for a shared template.
- Reuse successful interaction patterns conceptually, but rewrite structure, wording, layout, and visual direction for the current repository.
- Match the demo to the repo's nature:
  - backend/pipeline repo: emphasize flow, branching, data transformations
  - frontend/product repo: emphasize screens, user journey, state transitions
  - infrastructure repo: emphasize environments, deploy stages, service relationships
- Keep the visual language intentional. Avoid generic white-card dashboards.
- Preserve an existing docs/design system if the repo already has one.

## Content Rules

- Tie each step to concrete code references.
- Keep explanatory text short and high signal.
- Prefer one strong narrative over exhaustive coverage.
- Call out optional branches explicitly instead of burying them in prose.
- If information is uncertain, inspect more code before inventing a story.

## Mermaid Rules

- Use Mermaid syntax that is easy to regenerate from code findings.
- Prefer flowcharts unless another Mermaid diagram type is materially better.
- Keep node labels short.
- Highlight the active step if the page has a current-step interaction model.
- Make the diagram area zoomable or fit-to-viewport when it contains enough nodes to become cramped.

## Implementation Guidelines

- Use a single self-contained HTML file by default.
- Keep JavaScript readable and local to the page unless the repo already has a modular frontend structure.
- Make the layout responsive without relying on fixed diagram dimensions.
- If Mermaid is loaded from a CDN, mention that in the final response.
- If the user asks for a fully offline page, vendor the dependency or replace Mermaid rendering accordingly.

## Deliverable Checklist

- The page explains the repository's real flow.
- The interaction model is obvious without extra instructions.
- The Mermaid graph is legible on the user's viewport.
- The page is visually distinct enough to feel designed for this repo.
- The final response names the output path and any important runtime constraints.
