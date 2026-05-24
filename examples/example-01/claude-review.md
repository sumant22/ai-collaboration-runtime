# Claude Review — Example 01

> This is a realistic sample of what Claude should produce when given the
> chatgpt-response.md and asked to apply review + verification skills.
> In real use, replace this with Claude's actual output.

---

## Reviewed Task
Design a data backup strategy for a small SaaS product.

## Reviewer
Claude

## Review Date
[Date of actual review]

---

## Review (Review Skill)

### Summary
The proposed backup plan is well-structured, clearly within budget, and
executable by a small non-DevOps team. The major gap is the lack of
RDS cross-region failover, which the implementer correctly flagged.
The plan is appropriate for a low-risk early-stage SaaS but needs one
explicit decision from the team before approval.

### Findings

1. **RDS PITR is correctly recommended** — this is the right tool for
   database recovery and the 45-minute restore time is realistic.

2. **S3 Cross-Region Replication is appropriate** — covers the most
   likely file loss scenarios at low cost.

3. **The RDS region outage gap is a real risk** — the implementer
   flagged it honestly. This is not an oversight; it is a budget constraint.
   The team needs to decide if this risk is acceptable.

4. **Recovery drill is included** — this is often skipped and its
   inclusion here is correct. A plan without a tested recovery is not a
   real backup plan.

5. **RPO is not defined** — the request did not specify RPO, and the
   implementer listed it as unknown. This should be resolved before implementation,
   as it affects snapshot frequency decisions.

6. **Runbook is included** — Step 11 creates team documentation.
   Good operational practice, correctly included.

### Risks

- **RTO claim is partially incorrect**: The verification table says
  "Partial — full region failover NOT covered." This is honest, but the
  recommendation says "Approve." This is a mild inconsistency. The recommendation
  should say "Approve with conditions" more explicitly.

- **No mention of backup encryption** — RDS snapshots are encrypted if
  the source DB is encrypted, but this was not verified or mentioned.
  For a SaaS with customer data, this is worth confirming.

- **Snapshot retention period not justified** — 7 days is chosen but
  not explained. Is this sufficient for the business? Some compliance
  requirements need 30-90 days.

### Recommendation
**Needs Revision** — minor revision only. Three items need resolution:
1. Confirm RDS encryption status
2. Justify or increase snapshot retention period with team input
3. Get explicit team decision on RDS cross-region risk acceptance

---

## Verification (Verification Skill)

### Verified Areas
- Cost estimates are realistic and within budget ✓
- RDS PITR achieves sub-1-hour RTO for most failure scenarios ✓
- S3 versioning + CRR covers accidental deletion and file loss ✓
- All steps use AWS console — executable without DevOps specialist ✓
- Recovery drill is present and has a clear success criterion ✓

### Concerns
- RTO for full region outage is NOT under 1 hour with this plan
- Backup encryption not addressed
- Snapshot retention period not justified against business requirements

### Missing Information
- RPO (recovery point objective) — never defined in request or response
- RDS encryption status of current database
- Any compliance requirements (GDPR, SOC2, etc.) that affect retention

### Confidence Level
**Medium** — the plan is solid for common failure scenarios. It has
known gaps that were honestly identified. The gaps are resolvable with
two short decisions from the team.

---

## Escalation Required?
No — this does not need human escalation. It needs a revision pass on
three specific items, then it is ready to approve.
