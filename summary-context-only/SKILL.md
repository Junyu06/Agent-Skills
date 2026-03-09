---
name: summary-context-only
description: Summarize only the current conversation context window into a dense structured handoff and prepare a new-chat starter message. Use when the user invokes /summary or asks for context-window summarization for handoff, continuation, or session reset. During summarization, do not call any external tools, do not read files, and do not fetch new information.
---

# Summary Context Only

Summarize the existing context window only. Produce a compact, technical handoff that can be pasted into a new chat.

## Hard Constraints

- Use only information already present in the current context window.
- Do not call any external tools during summarization.
- Do not search the web.
- Do not read files.
- Do not infer missing facts as true; mark unknowns explicitly.
- Do not paraphrase line by line.
- Compress aggressively and avoid repetitive wording.

## Execution Workflow

1. Identify input type from context:
- conversation history
- code discussion
- debugging thread
- planning/decision thread

2. Extract only high-value signal:
- objective and scope
- decisions made
- key evidence and constraints
- unresolved blockers
- next actionable steps

3. Produce output in the required format below.

4. End with a `New Chat Seed` block that can be pasted as the first message in a new chat.

## Output Format

### Overview
1-3 sentences: core objective, current status, and what must happen next.

### Key Points
- Bullet list of critical facts only.

### Decisions Made
- Bullet list of committed choices and rationale.

### Open Issues
- Bullet list of unresolved questions, risks, or blockers.

### Next Actions
- Numbered list of concrete next steps.

### New Chat Seed
Provide a single paste-ready message that includes:
- task goal
- compact project context
- current constraints
- exact immediate next step request

## Style

- Prefer bullets over paragraphs.
- Keep language technical and dense.
- Avoid filler and motivational phrasing.
- Keep output concise but complete for handoff.
