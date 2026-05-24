# Task Response — ChatGPT (Example 01)

> This is a realistic sample of what ChatGPT should produce when given the
> task-request.md and asked to apply reasoning + planning skills.
> In real use, replace this with ChatGPT's actual output.

---

## Task Reference
Design a data backup strategy for a small SaaS product.

## Skills Applied
- reasoning
- planning

## Analysis

### Known Facts
- PostgreSQL database (~20GB, growing 5GB/month)
- File uploads on S3
- 3-person team, no DevOps specialist
- AWS cloud provider
- No backups currently exist
- RTO requirement: under 1 hour
- Budget cap: $100/month

### Assumptions
- Using Amazon RDS for PostgreSQL (managed), not self-hosted EC2
- S3 bucket contains user-uploaded files, not application code
- Team has basic AWS console access
- Recovery drill has never been performed

### Unknowns
- Recovery Point Objective (RPO) — how much data loss is acceptable?
- Whether RDS Multi-AZ is already enabled
- Retention period required for compliance or business reasons

## Proposed Approach

### Phase 1 — Database Backup (Week 1)

| Step | Action | Tool | Est. Cost | Success Criteria |
|------|--------|------|-----------|-----------------|
| 1 | Enable automated daily RDS snapshots with 7-day retention | RDS Automated Backups | ~$5/mo | Snapshot visible in RDS console next day |
| 2 | Enable Point-In-Time Recovery (PITR) | RDS PITR (included with automated backups) | $0 extra | PITR enabled shown in RDS settings |
| 3 | Enable RDS deletion protection | RDS setting | $0 | Protection enabled — prevents accidental DB delete |

### Phase 2 — File Storage Backup (Week 1)

| Step | Action | Tool | Est. Cost | Success Criteria |
|------|--------|------|-----------|-----------------|
| 4 | Enable S3 versioning on upload bucket | S3 Versioning | $2-5/mo | Versioning status: Enabled |
| 5 | Configure S3 Cross-Region Replication to us-west-2 | S3 CRR | ~$10/mo | Files replicated within 15 min of upload |
| 6 | Set lifecycle rule: delete old versions after 30 days | S3 Lifecycle | $0 | Cost stays controlled |

### Phase 3 — Monitoring and Alerts (Week 2)

| Step | Action | Tool | Est. Cost | Success Criteria |
|------|--------|------|-----------|-----------------|
| 7 | Set up CloudWatch alarm for RDS snapshot failure | CloudWatch | ~$1/mo | Alert fires on test failure |
| 8 | Set up S3 replication failure notification | S3 Event + SNS | ~$1/mo | Notification received on test |

### Phase 4 — Recovery Drill (Week 3)

| Step | Action | Tool | Est. Cost | Success Criteria |
|------|--------|------|-----------|-----------------|
| 9 | Restore RDS snapshot to test instance | RDS restore | ~$3 one-time | Full restore completes under 45 minutes |
| 10 | Download and verify a sample S3 file from replica | Manual | $0 | File accessible and intact |
| 11 | Document recovery steps in team runbook | Markdown doc | $0 | Runbook reviewed by all 3 engineers |

**Total estimated monthly cost: ~$19-22/month**

## Risks

| Risk | Probability | Impact | Mitigation |
|------|------------|--------|-----------|
| Database corruption | Low | High | PITR allows restore to any second in last 35 days |
| Accidental table/data deletion | Medium | High | PITR + deletion protection covers this |
| S3 file accidental deletion | Medium | Medium | S3 versioning allows recovery of deleted files |
| AWS region outage (us-east-1) | Very Low | High | S3 CRR to us-west-2 covers files; RDS cross-region is not included in this budget — flag for future |
| RDS region outage | Very Low | Critical | Not fully covered in this plan — would require RDS read replica in second region (~$40/mo extra) |

## Verification

| Check | Result |
|-------|--------|
| Meets RTO under 1 hour? | Partial — RDS restore from snapshot takes 20-45 min; PITR similar. File recovery is near-instant from replica. Full region failover NOT covered. |
| Within $100/month budget? | Yes — estimated $19-22/month |
| All failure scenarios have mitigation? | Partial — region-level RDS outage has no mitigation in current budget |
| Executable by non-DevOps engineer? | Yes — all steps use AWS console, no CLI or scripts required |

## Confidence
Medium — core backup needs are covered well within budget, but full region
outage for the database has no mitigation at this budget level.

## Final Recommendation
Approve with one flag: the team should explicitly decide whether RDS
cross-region resilience is required. If yes, budget needs to increase by ~$40/month.
If acceptable risk, current plan is ready to implement.
