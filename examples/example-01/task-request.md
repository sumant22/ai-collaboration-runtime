# Task Request — Example 01

## Task
Design a data backup strategy for a small SaaS product.

## Objective
A clear, implementable backup plan that protects customer data with
recovery possible within 1 hour of any failure.

## Context
- Product: SaaS web app with PostgreSQL database and file uploads stored in S3
- Team size: 3 engineers, no dedicated DevOps person
- Current state: no automated backups exist today
- Cloud provider: AWS
- Database size: approximately 20GB currently, growing ~5GB/month

## Constraints
- Must not require a dedicated DevOps engineer to maintain day-to-day
- Recovery time objective (RTO): under 1 hour for any failure scenario
- Budget: under $100/month for all backup infrastructure
- Cannot use on-premise or self-hosted storage solutions

## Required Skills
- reasoning
- planning

## Expected Output
- Structured plan using planning skill output format (phases + step table)
- Specific AWS service recommendations with rationale for each
- Cost estimate per component adding to a monthly total
- Risk section covering at minimum: database corruption, accidental deletion, region outage

## Verification Requirements
- Verify the proposed RTO of under 1 hour is actually achievable with the tools chosen
- Verify all cost estimates together stay within $100/month
- Verify no failure scenario in the risk section is left without a mitigation
- Confirm each step is executable by a non-DevOps engineer
