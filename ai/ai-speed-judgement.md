---
title: AI Developer Speed and Judgement
tags: [ai, technique]
summary: Notes on how AI changes the nature of developer work — categorized as faster, further, or afresh — with practical principles for effective delegation to AI agents. Reach for it when evaluating AI adoption or coaching teams on how to work with agents.
related: [code-reviews, shifting-judgement-left]
---

# AI Developer Speed and Judgement

## Quick Anecdote

When factories were first electrified, almost nothing happened. Owners pulled the steam engine out, dropped an electric motor in its place, and left the machines where they were, still arranged around the old central driveshaft. Productivity barely moved, for decades. The payoff came later, once the work itself had been rebuilt around what electricity could actually do, with a small motor on every machine, instead of one dynamo turning the whole floor.

Think about what this looks like with AI in software.

## Is there anything you can now do at work because of AI that you couldn't do before?

3 zones:

1. Faster: familiar work like writing documentation or authoring tests, just now done more quickly. 45% of the responses fit into this bucket.
2. Further work that had been out of reach, either because it needed skills or capacity the developer didn't have, or because it was never worth the effort. 36.9% of tasks landed here.
3. Afresh was work that didn't exist before, largely built around directing agents and setting the standards their output has to meet. That accounted for 12.4%. The remaining 5.7% named no specific task.

Faster example:
Documentation drafted in minutes, root cause analysis under pressure, test coverage in an afternoon.

Further example:
Automating a task in an hour that would have taken a sprint to do manually.

Afresh example:
New work created around AI (skills, harness, loops, etc)

## Where to start

- **Show, don't just instruct.** "Handle errors better" tells an agent almost nothing. A pair of examples, one that meets your team's standard and one that nearly does, tells it where the line actually falls.
- **Size delegation to what you can verify.** Split work so the part you hand over matches the part you can check. The failure mode is delegating more than you can verify, then signing off because you assume the agent got it right, not because you've verified the result.
- **Judge AI's work against an independent standard.** Use requirements, tests, evaluations, and reviewers to challenge the result. A different model can help, but another agent agreeing is not enough. The checks still need to establish whether the work meets the intended behavior.
