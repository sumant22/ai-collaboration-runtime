# Task Response — Claude (Example 02)

## Task Reference
Plan how to organize customer follow-ups for a small retail shop.

## Skills Applied
- reasoning
- planning

---

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

---

## Proposed Approach

### Goal
Every customer inquiry is logged, followed up on time, and nothing is forgotten —
using only WhatsApp and Google Sheets, in under 15 minutes per day.

### Constraints
- Free tools only
- Max 15 min/day
- Non-technical staff can run it

---

### Phase 1 — Set Up The Tracker (One Time, 20 minutes)

| Step | Action | Tool | Success Criteria |
|------|--------|------|-----------------|
| 1 | Create a Google Sheet called "Customer Follow-ups" | Google Sheets (free) | Sheet exists and is shared with staff |
| 2 | Add these columns: Name, Phone, Inquiry, Date, Status, Next Follow-up Date | Google Sheets | Columns are set up |
| 3 | Set Status options: New / Contacted / Interested / Closed / Lost | Google Sheets | Written at top of sheet as reference |
| 4 | Share sheet link with all staff via WhatsApp | WhatsApp | All staff can open and edit the sheet |

---

### Phase 2 — Daily Routine (Every Day, 10-15 minutes)

| Step | Time | Action | Tool | Success Criteria |
|------|------|--------|------|-----------------|
| 1 | Morning (5 min) | Open sheet, check "Next Follow-up Date" column for today | Google Sheets | Know exactly who to contact today |
| 2 | Morning (5 min) | Send follow-up WhatsApp message to each customer due today | WhatsApp | Message sent, customer replied or noted as no reply |
| 3 | Evening (5 min) | Log any new inquiries received today into the sheet | Google Sheets | Every new inquiry from today is in the sheet |
| 4 | Evening (2 min) | Update Status for any customer who replied or decided today | Google Sheets | Sheet reflects today's reality |

---

### Phase 3 — Simple Follow-up Message Template (Use Every Time)

Save this in WhatsApp Saved Messages so staff can copy-paste:

```
Hello [Name], this is [Your Name] from Next Generation Door.
Just checking if you had any questions about the [door type] you inquired about.
We are happy to help. Let us know when is a good time to talk.
```

---

### Risks and Blockers

| Risk | Likelihood | Mitigation |
|------|-----------|------------|
| Staff forgets to update sheet | Medium | Owner checks sheet every evening — takes 2 min |
| Too many inquiries to track in sheet | Low | If over 20/day, switch to a free CRM like HubSpot Free |
| Staff has no internet for Sheets | Low | Use a paper notebook as backup with same columns |
| Customer doesn't reply to follow-up | Common | Mark as "No Reply" — follow up again after 3 days, max 3 attempts |

---

### Decision Points
- If daily inquiries exceed 20 → upgrade to HubSpot Free CRM (still free)
- If staff cannot use Google Sheets → switch to paper notebook with same column structure

---

## Verification

| Check | Result |
|-------|--------|
| Takes under 15 min/day? | Yes — Phase 2 routine is 10-15 min total |
| No paid tools needed? | Yes — Google Sheets is free with any Gmail account |
| Non-technical staff can run it? | Yes — copy-paste template + update 2 fields per customer |

---

## Confidence
High — this is a simple system using tools the shop likely already has.
No assumptions affect the core approach.

## Final Recommendation
Approve — set up the Google Sheet today (20 min one-time effort),
start the daily routine tomorrow morning.
