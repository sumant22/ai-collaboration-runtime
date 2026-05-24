# Example 01 — SaaS Backup Strategy

## What This Example Shows

A complete end-to-end collaboration cycle:

1. Human creates a task request
2. **ChatGPT** generates the response using reasoning + planning skills
3. **Claude** reviews the response using review + verification skills
4. Confidence rules determine the final decision

## Files In This Example

| File | Created By | Purpose |
|------|-----------|---------|
| task-request.md | Human | The problem to solve |
| chatgpt-response.md | ChatGPT | The proposed solution |
| claude-review.md | Claude | Review and verification |
| final-decision.md | Human (using confidence rules) | Outcome |

## How To Replicate This

1. Copy `task-request.md` content → paste into ChatGPT with the message:
   > "Apply the reasoning skill and planning skill. Respond using the Task Response Protocol format."

2. Copy ChatGPT's response into `chatgpt-response.md`

3. Paste `chatgpt-response.md` into Claude with the message:
   > "Apply the review skill and verification skill to this Task Response. Use the Review Output format."

4. Copy Claude's review into `claude-review.md`

5. Apply `confidence-rules.md` to determine the final decision

6. Fill in `final-decision.md`
