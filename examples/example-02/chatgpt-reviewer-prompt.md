# ChatGPT Reviewer Prompt — Example 02

Copy and paste this entire message into ChatGPT to get the review.

---

```
Please read and load these skill files before we begin:

Review Skill: https://raw.githubusercontent.com/sumant22/ai-collaboration-runtime/main/skills/review/SKILL.md
Verification Skill: https://raw.githubusercontent.com/sumant22/ai-collaboration-runtime/main/skills/verification/SKILL.md
Confidence Rules: https://raw.githubusercontent.com/sumant22/ai-collaboration-runtime/main/decision-engine/confidence-rules.md

Your role is: Reviewer
Confirm when loaded. Then I will share the response to review.
```

---

After ChatGPT confirms, paste this second message:

---

```
Apply the review skill and verification skill to the response below.

Use this exact output format:

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

--- ORIGINAL TASK REQUEST ---

## Task
Plan how to organize customer follow-ups for a small retail shop.

## Objective
A simple, actionable system so no customer inquiry or follow-up is missed,
using tools the shop owner already has (WhatsApp and a basic notebook).

## Context
- Small retail shop selling steel doors
- Owner handles sales alone with 1-2 staff
- Customers inquire via WhatsApp, phone call, or walk-in
- Currently no system — follow-ups are forgotten sometimes
- No budget for paid software

## Constraints
- Must use only free tools (WhatsApp, Google Sheets, or paper notebook)
- Must be simple enough for non-technical staff to follow daily
- Cannot require more than 15 minutes per day to maintain

--- CLAUDE'S RESPONSE TO REVIEW ---

## Task Reference
Plan how to organize customer follow-ups for a small retail shop.

## Skills Applied
- reasoning
- planning

## Analysis

### Known Facts
- Shop: Next Generation Door, sells steel doors
- Team: owner + 1-2 staff
- Inquiry channels: WhatsApp, phone call, walk-in
- Current state: no system, follow-ups sometimes missed
- Budget: zero — free tools only
- Time available: max 15 minutes per day

### Assumptions
- Owner or staff have a smartphone with WhatsApp
- Owner has access to Google Sheets (free with Gmail account)
- Most customer conversations happen over WhatsApp already
- Customers typically need 1-3 follow-ups before deciding to buy

### Unknowns
- How many new inquiries come in per day on average
- Whether staff can access Google Sheets on their phone
- How long a typical sales cycle is (same day vs weeks)

## Proposed Approach

### Phase 1 — Set Up The Tracker (One Time, 20 minutes)

| Step | Action | Tool | Success Criteria |
|------|--------|------|-----------------|
| 1 | Create a Google Sheet called "Customer Follow-ups" | Google Sheets (free) | Sheet exists and shared with staff |
| 2 | Add columns: Name, Phone, Inquiry, Date, Status, Next Follow-up Date | Google Sheets | Columns set up |
| 3 | Set Status options: New / Contacted / Interested / Closed / Lost | Google Sheets | Written at top of sheet |
| 4 | Share sheet link with staff via WhatsApp | WhatsApp | All staff can open and edit |

### Phase 2 — Daily Routine (Every Day, 10-15 minutes)

| Step | Time | Action | Tool | Success Criteria |
|------|------|--------|------|-----------------|
| 1 | Morning (5 min) | Check "Next Follow-up Date" for today | Google Sheets | Know who to contact |
| 2 | Morning (5 min) | Send follow-up WhatsApp to each customer due today | WhatsApp | Message sent |
| 3 | Evening (5 min) | Log new inquiries received today | Google Sheets | All inquiries logged |
| 4 | Evening (2 min) | Update Status for customers who replied | Google Sheets | Sheet up to date |

### Phase 3 — Follow-up Message Template

Hello [Name], this is [Your Name] from Next Generation Door.
Just checking if you had any questions about the [door type] you inquired about.
We are happy to help. Let us know when is a good time to talk.

## Risks

| Risk | Likelihood | Mitigation |
|------|-----------|------------|
| Staff forgets to update sheet | Medium | Owner checks sheet every evening |
| Too many inquiries | Low | Switch to HubSpot Free CRM |
| No internet for Sheets | Low | Use paper notebook as backup |
| Customer does not reply | Common | Follow up after 3 days, max 3 attempts |

## Verification

| Check | Result |
|-------|--------|
| Takes under 15 min/day? | Yes — 10-15 min total |
| No paid tools needed? | Yes — Google Sheets is free |
| Non-technical staff can run it? | Yes — copy-paste template + update 2 fields |

## Confidence
High — simple system using tools already available.

## Final Recommendation
Approve — set up the Google Sheet today, start daily routine tomorrow.
```
