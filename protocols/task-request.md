# Task Request Protocol

A structured format for requesting work from any AI in the collaboration runtime.
Fill every field. If a field is not applicable, write "N/A" — never leave fields blank.

---

## Field Descriptions

| Field | What to Write |
|-------|--------------|
| **Task** | One sentence describing what needs to be done |
| **Objective** | The outcome you want — what does success look like? |
| **Context** | Background information the AI needs to understand the problem |
| **Constraints** | Hard limits — time, scope, technology, things to avoid |
| **Required Skills** | Which skills from /skills/ the AI should apply |
| **Expected Output** | Exact format and content of what you want back |
| **Verification Requirements** | What the reviewing AI should check in the response |

---

## Template

```
## Task
[One sentence]

## Objective
[What does success look like?]

## Context
[Background, existing state, relevant facts]

## Constraints
[Hard limits — what must NOT happen, what scope is excluded]

## Required Skills
[List skills from /skills/ — e.g. reasoning, planning, verification]

## Expected Output
[Format: bullet list / table / structured markdown / code]
[Content: what sections or elements must be present]

## Verification Requirements
[What the reviewer must check]
```

---

## Filled Example

```
## Task
Design a data backup strategy for a small SaaS product.

## Objective
A clear, implementable backup plan that protects customer data
with recovery possible within 1 hour of any failure.

## Context
- SaaS web app with PostgreSQL database and file uploads (S3)
- Team size: 3 engineers
- Current state: no automated backups exist
- Budget: low — prefer managed/cloud solutions

## Constraints
- Must not require a dedicated DevOps engineer to maintain
- Recovery time objective (RTO): under 1 hour
- Budget: under $100/month
- Cannot use on-premise storage

## Required Skills
- reasoning
- planning

## Expected Output
- Structured plan with phases and steps
- Specific tool recommendations with rationale
- Cost estimate per component
- Risk section covering data loss scenarios

## Verification Requirements
- Verify RTO of 1 hour is achievable
- Verify all costs are within $100/month budget
- Check for missing failure scenarios
- Confirm plan is executable by 3-person team
```
