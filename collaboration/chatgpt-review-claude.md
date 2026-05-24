# Workflow — ChatGPT Implements, Claude Reviews

## When To Use This Workflow
- You want a second opinion on a plan, proposal, or solution
- You want to catch gaps, wrong assumptions, or missing risks
- You want a confidence level before acting on AI output

---

## Step 1 — Prepare the Task Request

Fill in `/protocols/task-request.md` completely.
Save it as your active task in `/workspace/current-task.md`.

---

## Step 2 — Generate With ChatGPT

Open ChatGPT. Paste this prompt:

```
I am using the AI Collaboration Runtime.

Please apply the following skills:
- Reasoning Skill (identify facts, assumptions, unknowns first)
- Planning Skill (produce a sequenced plan with steps and success criteria)

Then respond using the Task Response Protocol format:
- Task Reference
- Skills Applied
- Analysis (Known Facts / Assumptions / Unknowns)
- Proposed Approach
- Risks
- Verification table
- Confidence level
- Final Recommendation

Here is the task:

[paste your filled task-request.md here]
```

Save ChatGPT's full response in:
`/workspace/chatgpt-response.md` or `/examples/your-task/chatgpt-response.md`

---

## Step 3 — Review With Claude

Open Claude. Paste this prompt:

```
I am using the AI Collaboration Runtime.

Please apply the following skills:
- Review Skill (evaluate correctness, simplicity, alignment with goal)
- Verification Skill (validate claims, check for gaps, assess confidence)

Use the Review Output format:
- Summary
- Findings (numbered)
- Risks
- Recommendation (Approve / Needs Revision / Reject)

Then use the Verification Output format:
- Verified Areas
- Concerns
- Missing Information
- Confidence Level (High / Medium / Low)

Here is the original task request:
[paste task-request.md]

Here is the response to review:
[paste chatgpt-response.md]
```

Save Claude's review in:
`/workspace/review-output.md` or `/examples/your-task/claude-review.md`

---

## Step 4 — Apply Confidence Rules

Open `/decision-engine/confidence-rules.md`.

Compare:
- ChatGPT's Final Recommendation
- Claude's Recommendation
- Claude's Confidence Level

Use the Disagreement Handling table to determine the outcome.

---

## Step 5 — Record Final Decision

Fill in `/workspace/final-decision.md` with:
- The confidence level
- Whether they agreed
- The decision (Approve / Revise / Escalate)
- Revision scope if applicable

---

## Summary

```
Human fills task-request.md
        ↓
ChatGPT applies reasoning + planning → chatgpt-response.md
        ↓
Claude applies review + verification → claude-review.md
        ↓
Human applies confidence-rules.md → final-decision.md
```
