# Installation Guide

Two ways to install the AI Collaboration Runtime.
**Option B (GitHub) is recommended** — no re-uploading ever.

---

## Option A — Manual File Upload (quick start)

### ChatGPT
1. Go to [chatgpt.com](https://chatgpt.com) → **Projects** → **New Project**
2. Name it: `AI Collaboration Runtime`
3. Click **"Add files"** and upload:
   - `skills/reasoning/SKILL.md`
   - `skills/planning/SKILL.md`
   - `skills/review/SKILL.md`
   - `skills/verification/SKILL.md`
   - `protocols/task-request.md`
   - `protocols/task-response.md`
   - `decision-engine/confidence-rules.md`
   - `collaboration/claude-implements-chatgpt-reviews.md`
   - `collaboration/chatgpt-review-claude.md`

### Claude
1. Go to [claude.ai](https://claude.ai) → **Projects** → **Create Project**
2. Name it: `AI Collaboration Runtime`
3. Upload the same files listed above

---

## Option B — GitHub Raw Links (recommended)

Upload once to GitHub. Use permanent raw links in any chat.
No re-uploading when you update a skill — just push to GitHub.

### Step 1 — Upload to GitHub

1. Go to [github.com](https://github.com) → **New repository**
2. Name it: `ai-collaboration-runtime`
3. Set to **Public** (required for raw links to work)
4. Upload all files from the extracted zip

### Step 2 — Your Raw Links

Replace `YOUR_USERNAME` with your GitHub username.
These links never change even when you update the files.

```
Skills:
https://raw.githubusercontent.com/YOUR_USERNAME/ai-collaboration-runtime/main/skills/reasoning/SKILL.md
https://raw.githubusercontent.com/YOUR_USERNAME/ai-collaboration-runtime/main/skills/planning/SKILL.md
https://raw.githubusercontent.com/YOUR_USERNAME/ai-collaboration-runtime/main/skills/review/SKILL.md
https://raw.githubusercontent.com/YOUR_USERNAME/ai-collaboration-runtime/main/skills/verification/SKILL.md

Protocols:
https://raw.githubusercontent.com/YOUR_USERNAME/ai-collaboration-runtime/main/protocols/task-request.md
https://raw.githubusercontent.com/YOUR_USERNAME/ai-collaboration-runtime/main/protocols/task-response.md

Decision Engine:
https://raw.githubusercontent.com/YOUR_USERNAME/ai-collaboration-runtime/main/decision-engine/confidence-rules.md

Workflows:
https://raw.githubusercontent.com/YOUR_USERNAME/ai-collaboration-runtime/main/collaboration/claude-implements-chatgpt-reviews.md
https://raw.githubusercontent.com/YOUR_USERNAME/ai-collaboration-runtime/main/collaboration/chatgpt-review-claude.md
```

### Step 3 — Load In Claude (Implementer)

Paste this at the start of any Claude chat:

```
Please read and load these skill files before we begin:

Reasoning: https://raw.githubusercontent.com/YOUR_USERNAME/ai-collaboration-runtime/main/skills/reasoning/SKILL.md
Planning: https://raw.githubusercontent.com/YOUR_USERNAME/ai-collaboration-runtime/main/skills/planning/SKILL.md
Task Response Protocol: https://raw.githubusercontent.com/YOUR_USERNAME/ai-collaboration-runtime/main/protocols/task-response.md

Your role is: Implementer
Confirm when loaded. Then wait for my task.
```

### Step 4 — Load In ChatGPT (Reviewer)

Paste this at the start of any ChatGPT chat:

```
Please read and load these skill files before we begin:

Review Skill: https://raw.githubusercontent.com/YOUR_USERNAME/ai-collaboration-runtime/main/skills/review/SKILL.md
Verification Skill: https://raw.githubusercontent.com/YOUR_USERNAME/ai-collaboration-runtime/main/skills/verification/SKILL.md
Confidence Rules: https://raw.githubusercontent.com/YOUR_USERNAME/ai-collaboration-runtime/main/decision-engine/confidence-rules.md

Your role is: Reviewer
Confirm when loaded. Then wait for the response to review.
```

---

## Verify Installation

Send this in either Claude or ChatGPT after loading:

```
List all the skills and protocols you have loaded.
Summarize each in one sentence.
State your current role (Implementer or Reviewer).
```

You should see all loaded skills listed with their purpose.

---

## Recommended First Run

1. Open `examples/example-01/README.md`
2. Follow the steps — it walks through a complete Claude → ChatGPT review cycle
3. Compare your real outputs to the sample files provided

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| AI doesn't follow skill format | Say: *"Apply the reasoning skill you loaded"* |
| Raw link not loading | Check repo is Public on GitHub |
| ChatGPT and Claude disagree | Expected — apply `confidence-rules.md` to decide |
| A skill is missing | Re-paste that specific raw link and ask AI to load it |
