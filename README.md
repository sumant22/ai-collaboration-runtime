# AI Collaboration Runtime

> A shared skills, protocols and decision layer for reliable AI collaboration across Claude, ChatGPT, Cursor and Gemini.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
![Version](https://img.shields.io/badge/version-v1.0-blue)
![Status](https://img.shields.io/badge/status-active-brightgreen)

---

## What Is This?

Current AI systems are isolated. Each model reasons differently, verifies differently, and follows inconsistent workflows.

This project introduces a **shared collaboration layer** where multiple AI systems can:

- follow the same skills
- review each other's outputs
- verify results using shared protocols
- reach decisions using shared confidence rules

The goal is **not** autonomous AI agents.
The goal is **reliable, human-controlled collaborative intelligence**.

---

## How It Works

```
You fill task-request.md
        ↓
Claude applies reasoning + planning  →  generates response
        ↓
ChatGPT applies review + verification  →  reviews response
        ↓
You apply confidence-rules.md  →  final decision
```

Both AI systems use the same skills and protocols from this repository —
so their outputs are structured, comparable, and reviewable.

---

## Repository Structure

```
ai-collaboration-runtime/
├── AGENTS.md                   ← AI systems read this first
├── INSTALL.md                  ← Setup guide (GitHub raw links + manual)
├── skills/
│   ├── reasoning/SKILL.md      ← Break problems into facts, assumptions, unknowns
│   ├── planning/SKILL.md       ← Produce sequenced plans with success criteria
│   ├── review/SKILL.md         ← Evaluate outputs for correctness and clarity
│   └── verification/SKILL.md  ← Validate claims, check gaps, assess confidence
├── protocols/
│   ├── task-request.md         ← Structured format for requesting work
│   └── task-response.md        ← Structured format for responding to tasks
├── collaboration/
│   ├── claude-implements-chatgpt-reviews.md
│   └── chatgpt-review-claude.md
├── decision-engine/
│   └── confidence-rules.md     ← High / Medium / Low + disagreement handling
├── workspace/
│   ├── current-task.md
│   ├── review-output.md
│   └── final-decision.md
└── examples/
    └── example-01/             ← Complete worked example end to end
```

---

## Quick Start

### 1 — Load Skills Into Claude (Implementer role)

Paste this in a new Claude chat:

```
Please read and load these skill files:

Reasoning: https://raw.githubusercontent.com/sumant22/ai-collaboration-runtime/main/skills/reasoning/SKILL.md
Planning: https://raw.githubusercontent.com/sumant22/ai-collaboration-runtime/main/skills/planning/SKILL.md
Task Response Protocol: https://raw.githubusercontent.com/sumant22/ai-collaboration-runtime/main/protocols/task-response.md

Your role is: Implementer
Confirm when loaded. Then wait for my task.
```

### 2 — Give Claude Your Task

Use the task request format from `protocols/task-request.md`.

### 3 — Load Skills Into ChatGPT (Reviewer role)

Paste this in a new ChatGPT chat:

```
Please read and load these skill files:

Review Skill: https://raw.githubusercontent.com/sumant22/ai-collaboration-runtime/main/skills/review/SKILL.md
Verification Skill: https://raw.githubusercontent.com/sumant22/ai-collaboration-runtime/main/skills/verification/SKILL.md
Confidence Rules: https://raw.githubusercontent.com/sumant22/ai-collaboration-runtime/main/decision-engine/confidence-rules.md

Your role is: Reviewer
Confirm when loaded. Then wait for the response to review.
```

### 4 — Paste Claude's Response Into ChatGPT For Review

### 5 — Apply Confidence Rules → Make Final Decision

See `INSTALL.md` for the full setup guide.
See `examples/example-01/` for a complete worked example.

---

## Skills Overview

| Skill | Purpose | Used By |
|-------|---------|---------|
| Reasoning | Separates facts, assumptions, unknowns before solving | Implementer |
| Planning | Produces sequenced steps with dependencies and success criteria | Implementer |
| Review | Evaluates correctness, simplicity, alignment with goal | Reviewer |
| Verification | Validates claims, checks gaps, assigns confidence level | Reviewer |

---

## Confidence Levels

| Level | Meaning | Action |
|-------|---------|--------|
| High | Both AIs agree, all checks pass | Approve and proceed |
| Medium | Minor gaps, partial agreement | Revise specific areas only |
| Low | Conflicting recommendations or critical unknowns | Escalate to human |

---

## Works With

- Claude (claude.ai)
- ChatGPT (chatgpt.com)
- Cursor (via rules)
- Gemini
- Any AI that can read markdown files

---

## License

MIT — free to use, modify and share.
See [LICENSE](LICENSE).

---

## Version

v1.0 — first working runtime
