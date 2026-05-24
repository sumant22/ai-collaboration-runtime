# Final Decision — Example 01

## Task
Design a data backup strategy for a small SaaS product.

## Implementer AI
ChatGPT

## Reviewer AI
Claude

## Confidence Level
[x] Medium

## Agreement
[x] Partial agreement — both recommended revision, reviewer identified
    3 additional items the implementer did not address

## Decision
[x] Revise — revision scope:
    1. Confirm RDS encryption is enabled on current database
    2. Decide snapshot retention period (7 days vs 30 days)
    3. Team explicitly accepts or rejects the RDS cross-region risk
    4. Define RPO before implementation begins

After revision on these 4 points only, plan can be approved without
another full review cycle.

## Notes
Both AIs agreed the core approach is correct and within budget.
The disagreement was on completeness, not on approach direction.
This is a Medium confidence outcome per confidence-rules.md — revise
specific weak areas only, do not restart.

## Date
[Date]
