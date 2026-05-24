# AGENTS.md — AI Collaboration Runtime

This file tells any AI system how to load and use this repository correctly.

---

## What This Repository Is

A shared behavioral runtime for AI collaboration.

It gives multiple AI systems (Claude, ChatGPT, Cursor, Gemini, local models)
the same skills, protocols, and decision rules so they can:

- generate solutions using shared skills
- review each other's outputs using shared protocols
- reach decisions using shared confidence rules

---

## How To Load This Runtime

When starting a session, read these files in order:

### 1. Skills (load all that apply to your role)

| Role | Skills To Load |
|------|---------------|
| Implementer | reasoning, planning |
| Reviewer | review, verification |
| Both | all four |

Skill file locations:
- `skills/reasoning/SKILL.md`
- `skills/planning/SKILL.md`
- `skills/review/SKILL.md`
- `skills/verification/SKILL.md`

### 2. Protocols (always load both)
- `protocols/task-request.md`
- `protocols/task-response.md`

### 3. Decision Rules
- `decision-engine/confidence-rules.md`

---

## Behavioral Rules For All AI Systems

- Always identify your role: Implementer or Reviewer
- Always use the Task Response Protocol format when responding to a task
- Always separate facts from assumptions in your analysis
- Never skip the Verification table in your response
- Never claim High confidence unless all three verification checks pass
- If information is missing, state it explicitly — do not assume or invent

---

## Workflows

Two collaboration workflows are available:

| Workflow | File |
|----------|------|
| Claude implements, ChatGPT reviews | `collaboration/claude-implements-chatgpt-reviews.md` |
| ChatGPT implements, Claude reviews | `collaboration/chatgpt-review-claude.md` |

---

## Workspace Files

Active task state is tracked in `/workspace/`:

| File | Purpose |
|------|---------|
| `current-task.md` | The task currently being worked on |
| `review-output.md` | The reviewer's output |
| `final-decision.md` | The final decision after applying confidence rules |

---

## Example

See `examples/example-01/` for a complete end-to-end run:
- filled task request
- sample implementer response
- sample reviewer output
- final decision

---

## Version
v1.0
