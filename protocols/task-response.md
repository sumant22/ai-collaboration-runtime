# Task Response Protocol

The standard output format for any AI responding to a Task Request.
Every response must follow this structure exactly so the reviewing AI can process it consistently.

---

## Field Descriptions

| Field | What to Write |
|-------|--------------|
| **Task Reference** | Copy the Task line from the request |
| **Skills Applied** | List which skills were used |
| **Analysis** | Your reasoning — facts, assumptions, unknowns |
| **Proposed Approach** | Your actual answer, plan, or solution |
| **Risks** | What could go wrong with this approach |
| **Verification** | Self-check — did you meet the objective and constraints? |
| **Confidence** | High / Medium / Low + one sentence reason |
| **Final Recommendation** | Clear, direct statement of what should happen next |

---

## Template

```
## Task Reference
[Copy task line from request]

## Skills Applied
- [skill name]

## Analysis

### Known Facts
-

### Assumptions
-

### Unknowns
-

## Proposed Approach
[Your solution, plan, or answer]

## Risks
-

## Verification

| Check | Result |
|-------|--------|
| Meets objective? | Yes / No / Partial |
| Within constraints? | Yes / No / Partial |
| Missing information? | Yes / No |

## Confidence
[High / Medium / Low] — [one sentence reason]

## Final Recommendation
[Approve / Revise / Escalate] — [one sentence explaining why]
```

---

## Filled Example

```
## Task Reference
Design a data backup strategy for a small SaaS product.

## Skills Applied
- reasoning
- planning

## Analysis

### Known Facts
- PostgreSQL + S3 storage
- 3-person team, no DevOps specialist
- No current backup system
- Budget cap: $100/month

### Assumptions
- Database size is under 100GB (typical for early SaaS)
- Team has basic AWS familiarity
- RDS or managed Postgres is in use (not self-hosted)

### Unknowns
- Exact database size and growth rate
- Current cloud provider (assumed AWS)
- Acceptable data loss window (RPO) — not specified in request

## Proposed Approach

### Phase 1 — Database Backups (Week 1)
| Step | Action | Tool | Cost | Success Criteria |
|------|--------|------|------|-----------------|
| 1 | Enable automated daily snapshots | RDS automated backups | ~$10/mo | Snapshot visible in console |
| 2 | Enable point-in-time recovery | RDS PITR | included | Recovery tested successfully |

### Phase 2 — File Backups (Week 2)
| Step | Action | Tool | Cost | Success Criteria |
|------|--------|------|------|-----------------|
| 3 | Enable S3 versioning | S3 built-in | free | Versioning enabled on bucket |
| 4 | Add cross-region replication | S3 replication | ~$15/mo | Files appear in secondary region |

### Phase 3 — Recovery Test (Week 3)
| Step | Action | Tool | Cost | Success Criteria |
|------|--------|------|------|-----------------|
| 5 | Run full recovery drill | Manual | $0 | Recovery completed under 1 hour |

Total estimated cost: ~$25-40/month

## Risks
- RPO not defined — assuming 24hr data loss acceptable; if not, needs review
- Recovery drill may reveal gaps not visible in planning
- AWS region outage could affect both primary and backup if same region used

## Verification

| Check | Result |
|-------|--------|
| Meets objective? | Yes — RTO under 1hr achievable with PITR |
| Within constraints? | Yes — estimated $25-40/mo, well under $100 |
| Missing information? | Yes — RPO not specified in request |

## Confidence
Medium — approach is sound but RPO assumption may be wrong.

## Final Recommendation
Approve with one revision: requester should confirm acceptable data loss
window (RPO) before implementing Phase 1.
```
