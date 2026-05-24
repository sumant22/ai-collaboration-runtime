# Task Response — Claude v2 (Example 02)
# Revised based on ChatGPT review findings

## Task Reference
Plan how to organize customer follow-ups for a small retail shop.

## Skills Applied
- reasoning
- planning

## What Changed From v1
| # | Change | Reason |
|---|--------|--------|
| 1 | Added example tracker row with sample data | Missing in v1 |
| 2 | Added paper notebook column layout | No concrete format in v1 |
| 3 | Added follow-up timing rule (default 3 days) | Column existed but no guidance |
| 4 | Added overdue follow-up handling step | Not addressed in v1 |
| 5 | Added owner vs staff responsibilities table | Implied but not defined in v1 |
| 6 | Removed HubSpot mention | Too complex for simplicity-first constraint |

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
- Owner and staff have smartphones with WhatsApp
- Owner has a Gmail account (Google Sheets is free with Gmail)
- Most customer conversations happen over WhatsApp already
- Customers typically need 1-3 follow-ups before deciding to buy

### Unknowns
- How many new inquiries come in per day on average
- How long a typical sales cycle is (same day vs weeks)

---

## Proposed Approach

### Responsibilities — Who Does What

| Task | Owner | Staff |
|------|-------|-------|
| Set up Google Sheet (one time) | ✓ | — |
| Morning check — who to follow up today | ✓ | ✓ |
| Send follow-up WhatsApp messages | ✓ | ✓ |
| Log new inquiries each evening | ✓ | ✓ |
| Update status after customer replies | ✓ | ✓ |
| Evening check — overdue leads | ✓ | — |
| Weekly review of Closed/Lost entries | ✓ | — |

---

### Phase 1 — Set Up The Tracker (One Time, 20 minutes)

| Step | Action | Tool | Success Criteria |
|------|--------|------|-----------------|
| 1 | Create a Google Sheet called "Customer Follow-ups" | Google Sheets (free) | Sheet exists and shared with staff |
| 2 | Add columns: Name, Phone, Inquiry, Channel, Date, Status, Next Follow-up Date, Attempts | Google Sheets | Columns set up |
| 3 | Set Status options at top: New / Contacted / Interested / Closed / Lost | Google Sheets | Reference visible on sheet |
| 4 | Add one sample row (see below) | Google Sheets | Staff understand the format |
| 5 | Share sheet link with all staff via WhatsApp | WhatsApp | All staff can open and edit on phone |

#### Example Sheet Row (sample data)

| Name | Phone | Inquiry | Channel | Date | Status | Next Follow-up Date | Attempts |
|------|-------|---------|---------|------|--------|-------------------|---------|
| Ravi Sharma | 9876543210 | Main door, 8ft, brown | WhatsApp | 24-May | Contacted | 27-May | 1 |
| Priya Kulkarni | 9823456789 | Front gate quote | Walk-in | 23-May | New | 24-May | 0 |

#### Follow-up Timing Rule
- **Default:** set Next Follow-up Date to **3 days** after last contact
- **Hot lead** (customer asked for price or measurements): follow up next day
- **No reply after 3 attempts:** mark Status as Lost, stop following up

---

### Phase 2 — Daily Routine (Every Day, 12-15 minutes)

| Step | Time | Who | Action | Tool | Success Criteria |
|------|------|-----|--------|------|-----------------|
| 1 | Morning (3 min) | Owner/Staff | Filter sheet by today's date in Next Follow-up Date column | Google Sheets | List of customers to contact today is clear |
| 2 | Morning (2 min) | Owner/Staff | Check for overdue rows — Next Follow-up Date is before today | Google Sheets | Overdue leads identified |
| 3 | Morning (5 min) | Owner/Staff | Send follow-up WhatsApp to each customer due today + overdue | WhatsApp | All messages sent, Attempts count updated |
| 4 | Evening (3 min) | Owner/Staff | Log any new inquiries received today | Google Sheets | Every new inquiry from today is in the sheet |
| 5 | Evening (2 min) | Owner | Update Status for customers who replied or decided today | Google Sheets | Sheet reflects today's reality |

#### Overdue Rule
If Next Follow-up Date is before today and Status is still New or Contacted:
- Contact immediately
- If Attempts = 3 → mark Status as Lost

---

### Phase 3 — Follow-up Message Templates

**WhatsApp follow-up (standard):**
```
Hello [Name], this is [Your Name] from Next Generation Door.
Just checking if you had any questions about the [door type] you inquired about.
We are happy to help. Let us know when is a good time to talk.
```

**WhatsApp follow-up (hot lead — asked for price):**
```
Hello [Name], this is [Your Name] from Next Generation Door.
I wanted to share the price for the [door type] you asked about — it is [price].
Let me know if you would like to proceed or need any changes.
```

**Phone call script (walk-in or phone inquiry):**
```
Hello, may I speak with [Name]?
This is [Your Name] from Next Generation Door.
You had inquired about [door type] — I just wanted to follow up
and check if you had any questions. Is this a good time?
```

---

### Phase 4 — Paper Notebook Backup (if no internet)

Use this column layout in any notebook:

```
| Name | Phone | Inquiry | Date | Status | Follow-up On | Attempts |
```

Rules for notebook:
- One row per customer
- Circle the row when follow-up is due today
- Cross out row when Closed or Lost
- Transfer to Google Sheet at end of day when internet is available

---

## Risks

| Risk | Likelihood | Mitigation |
|------|-----------|------------|
| Staff forgets to update sheet | Medium | Owner does evening review — takes 2 min |
| Duplicate entries from multiple channels | Medium | Check phone number before adding new row |
| Overdue leads missed | Low | Step 2 of morning routine catches these |
| No internet for Sheets | Low | Use paper notebook backup (Phase 4), sync later |
| Customer does not reply | Common | Max 3 attempts rule — then mark Lost |

---

## Verification

| Check | Result |
|-------|--------|
| Takes under 15 min/day? | Yes — 12-15 min total |
| No paid tools needed? | Yes — Google Sheets and WhatsApp are free |
| Non-technical staff can run it? | Yes — copy-paste templates + update 3 fields per customer |
| Walk-in inquiries covered? | Yes — Channel column + evening log step |
| Overdue leads handled? | Yes — morning Step 2 checks for overdue rows |
| Ownership defined? | Yes — responsibilities table at top |
| Follow-up timing defined? | Yes — default 3 days, hot lead next day, 3 attempts max |

---

## Confidence
High — all gaps from v1 review are addressed. No unknowns affect the core approach.

## Final Recommendation
Approve — all 6 revision items from ChatGPT review are resolved.
Ready to implement.
