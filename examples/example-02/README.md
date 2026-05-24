# Example 02 — Customer Follow-up System for Small Retail Shop

## What This Example Shows

A simple, real-world task run through the full collaboration cycle:

1. Human creates task request
2. **Claude** generates the plan (reasoning + planning skills)
3. **You** take Claude's response to ChatGPT for review
4. **ChatGPT** reviews using review + verification skills
5. You apply confidence rules → final decision

## Task
Plan a customer follow-up system for a small steel door retail shop
using only free tools (WhatsApp + Google Sheets).

## Files

| File | Purpose |
|------|---------|
| `task-request.md` | The task — filled and ready |
| `claude-response.md` | Claude's generated plan |
| `chatgpt-reviewer-prompt.md` | Copy-paste this into ChatGPT to get the review |
| `chatgpt-review.md` | Paste ChatGPT's review output here |
| `final-decision.md` | Fill this after applying confidence rules |

## How To Run This Example

### Step 1 — Claude already done
Claude's response is in `claude-response.md` — ready to review.

### Step 2 — Take to ChatGPT
Open `chatgpt-reviewer-prompt.md`
Copy the first message → paste into ChatGPT → wait for confirmation
Then copy the second message → paste → get the review

### Step 3 — Save ChatGPT's review
Paste ChatGPT's output into `chatgpt-review.md`

### Step 4 — Apply confidence rules
Open `decision-engine/confidence-rules.md`
Compare both recommendations → fill `final-decision.md`
