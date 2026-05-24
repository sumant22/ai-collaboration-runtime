# Workflow — Claude Implements, ChatGPT Reviews

## When To Use This Workflow
- You want Claude to generate the solution first
- You want ChatGPT to independently review and verify it
- You want a second opinion before acting

---

## The Flow

```
You fill task-request.md
        ↓
Claude applies reasoning + planning → generates response
        ↓
You copy Claude's response to ChatGPT for review
        ↓
ChatGPT applies review + verification → gives confidence level
        ↓
You apply confidence-rules.md → final decision
```

---

## Step 1 — Prepare Task Request

Fill in the task request using this template:

```
## Task
[One sentence]

## Objective
[What does success look like?]

## Context
[Background, existing state, relevant facts]

## Constraints
[Hard limits — what must NOT happen, what scope is excluded]

## Required Skills
- reasoning
- planning

## Expected Output
[Format and content you want back]

## Verification Requirements
[What the reviewer must check]
```

---

## Step 2 — Generate With Claude

Open Claude. If using GitHub, paste this as your first message:

```
Please read and load these skill files before we begin:

Reasoning: https://raw.githubusercontent.com/sumant22/ai-collaboration-runtime/main/skills/reasoning/SKILL.md
Planning: https://raw.githubusercontent.com/sumant22/ai-collaboration-runtime/main/skills/planning/SKILL.md
Task Response Protocol: https://raw.githubusercontent.com/sumant22/ai-collaboration-runtime/main/protocols/task-response.md

Confirm when loaded. Then wait for my task.
```

Once Claude confirms, paste this:

```
Apply the reasoning skill and planning skill.
Respond using the Task Response Protocol format exactly:

- Task Reference
- Skills Applied
- Analysis (Known Facts / Assumptions / Unknowns)
- Proposed Approach
- Risks
- Verification table
- Confidence level
- Final Recommendation

Here is the task:

[paste your filled task request here]
```

Save Claude's full response — you will paste it into ChatGPT next.

---

## Step 3 — Review With ChatGPT

Open ChatGPT. Paste this as your first message:

```
Please read and load these skill files before we begin:

Review Skill: https://raw.githubusercontent.com/sumant22/ai-collaboration-runtime/main/skills/review/SKILL.md
Verification Skill: https://raw.githubusercontent.com/sumant22/ai-collaboration-runtime/main/skills/verification/SKILL.md
Confidence Rules: https://raw.githubusercontent.com/sumant22/ai-collaboration-runtime/main/decision-engine/confidence-rules.md

Confirm when loaded. Then wait for the response to review.
```

Once ChatGPT confirms, paste this:

```
Apply the review skill and verification skill to the response below.

Use this output format exactly:

REVIEW:
- Summary
- Findings (numbered list)
- Risks
- Recommendation: Approve / Needs Revision / Reject

VERIFICATION:
- Verified Areas
- Concerns
- Missing Information
- Confidence Level: High / Medium / Low + one sentence reason

Here is the original task request:
[paste your task request]

Here is Claude's response to review:
[paste Claude's full response]
```

Save ChatGPT's review output.

---

## Step 4 — Apply Confidence Rules

Open `decision-engine/confidence-rules.md`

Compare:
- Claude's Final Recommendation
- ChatGPT's Recommendation
- ChatGPT's Confidence Level

Use the Disagreement Handling table to determine outcome.

---

## Step 5 — Record Final Decision

Fill in `workspace/final-decision.md`:

```
## Task
[Task reference]

## Implementer AI
Claude

## Reviewer AI
ChatGPT

## Confidence Level
[ ] High / [ ] Medium / [ ] Low

## Agreement
[ ] Both agreed / [ ] Disagreement — see notes

## Decision
[ ] Approved
[ ] Revise — revision scope: [describe]
[ ] Escalated — reason: [describe]

## Notes

## Date
```

---

## Tips

- If Claude says Medium or Low confidence in its own response,
  pay extra attention to ChatGPT's review — the gap is likely real
- If both AIs agree on Approve → High confidence, proceed
- If they disagree → do not guess, escalate to yourself as the human decision maker
- Never skip the Verification table — it is the most useful part of the output
