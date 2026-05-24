# Confidence Rules

Rules for determining confidence level and next action after a review cycle.
These rules are applied by the human or the reviewing AI after receiving a Task Response.

---

## Confidence Levels

### High Confidence
**Criteria — ALL of the following must be true:**
- Verification table shows "Yes" for all three checks
- Risks section contains no items marked as critical or blocking
- Both AI systems (implementer + reviewer) reached the same recommendation
- No unknowns listed that affect the core solution

**Action:** Approve and proceed.

---

### Medium Confidence
**Criteria — ANY of the following is true:**
- One verification check shows "Partial"
- Unknowns exist but do not change the core approach
- Minor disagreement between AI systems on one non-critical point
- Risks exist but are low probability or easily mitigated

**Action:** Revise the specific weak area only, then re-verify that section.
Do not restart from scratch.

---

### Low Confidence
**Criteria — ANY of the following is true:**
- Any verification check shows "No"
- A critical unknown makes the solution unverifiable
- AI systems disagree on the core recommendation (Approve vs Reject)
- A risk could cause total failure of the objective

**Action:** Escalate to human decision-maker with a clear summary of:
- What is known
- What is in conflict
- What decision is needed from the human

---

## Disagreement Handling

When two AI systems give different recommendations:

| Scenario | Action |
|----------|--------|
| Both say Approve | High confidence — proceed |
| One Approve, one Needs Revision | Medium — address revision items, re-review |
| One Approve, one Reject | Low — escalate to human |
| Both say Needs Revision | Medium — consolidate revision points, redo response |
| Both say Reject | Low — escalate with full context |

---

## Escalation Format

When escalating to a human, always provide:

```
## Escalation Summary

### Task
[Original task]

### What Is Known
-

### What Is In Conflict
-

### What The Human Needs To Decide
-

### Recommended Options
1.
2.
```
