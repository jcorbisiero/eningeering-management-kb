---
title: Auditing a Codebase
tags: [software-engineering, technique]
summary: Practical techniques for auditing an unfamiliar codebase — stakeholder interview questions, five git commands to surface churn, bus factor, and bug hotspots, and AI prompts for deeper analysis. Reach for it when taking over a codebase or running a technical due diligence.
related: []
---

# Auditing a Codebase

## Before You Clone the Repo: The Stakeholder Interview

Questions for developers:

- "What's the one area you're afraid to touch?"
- "When's the last time you deployed on a Friday?"
- "What broke in production in the last 90 days that wasn't caught by tests?"

Questions for the CTO/EM:

- "What feature has been blocked for over a year?"
- "Do you have real-time error visibility right now?"
- "What was the last feature that took significantly longer than estimated?"

Questions for business stakeholders:

- "Are there features that got quietly turned off and never came back?"
- "Are there things you've stopped promising customers?"

## Five git commands that can help

What changes the most:

```bash
git log --format=format: --name-only --since="1 year ago" | sort | uniq -c | sort -nr | head -20
```

- Run this from app/ or src/, not the repo root. Lockfiles, changelogs, and generated code will dominate the list otherwise.
- The command above is the absolute kind, so I take the top 5 files from this list and cross-reference them against the bug hotspot command below. A file that's high-churn and high-bug is your single biggest risk.

Who built this:

```bash
git shortlog -sn --no-merges
```

- If one person accounts for 60% or more, that's your bus factor
- If they left six months ago, it's a crisis
- If the top contributor from the overall shortlog doesn't appear in a 6-month window (git shortlog -sn --no-merges --since="6 months ago"), flag that to the client immediately.
- Also look at the tail. Thirty contributors but only three active in the last year. The people who built this system aren't the people maintaining it.
- One caveat: squash-merge workflows compress authorship. If the team squashes every PR into a single commit, this output reflects who merged, not who wrote. Worth asking about the merge strategy before drawing conclusions.

Where do bugs cluster:

```bash
git log -i -E --grep="fix|bug|broken" --name-only --format='' | sort | uniq -c | sort -nr | head -20
```

- Same shape as the churn command, filtered to commits with bug-related keywords
- Compare this list against the churn hotspots
- Files that appear on both are your highest-risk code: they keep breaking and keep getting patched, but never get properly fixed
- **Caveat**: This depends on commit message discipline. If the team writes "update stuff" for every commit, you'll get nothing. But even a rough map of bug density is better than no map.

Is the project accelerating or dying:

```bash
git log --format='%ad' --date=format:'%Y-%m' | sort | uniq -c
```

- Commit count by month, for the entire history of the repo
- Scan the output looking for shapes. A steady rhythm is healthy
- What does it look like when the count drops by half in a single month? Usually someone left. A declining curve over 6 to 12 months tells you the team is losing momentum. Periodic spikes followed by quiet months means the team batches work into releases instead of shipping continuously.

How often the team is firefighting:

```bash
git log --oneline --since="1 year ago" | grep -iE 'revert|hotfix|emergency|rollback'
```

- Revert and hotfix frequency. A handful over a year is normal.
- Reverts every couple of weeks means there is evidence of a deeper issue: unreliable tests, missing staging, or a deploy pipeline that makes rollbacks harder than they should be. Zero results is also a signal; either the team is stable, or nobody writes descriptive commit messages.

## How AI can help

### God model decomposition:

- This is a Rails model. List every distinct responsibility you can identify. Group related methods together and suggest what each group might be extracted into.

### Callback mapping:

- List every callback in this file, what it does, and what other models or side effects it might touch. Flag anything that looks like it could cause unexpected behavior.

### Test coverage gap analysis:

- What are the ten most important things to test in this file, in priority order?

One caveat: AI doesn't know what the business does. It can't tell you whether the complexity in Order is accidental or load-bearing. That judgment is still yours.
