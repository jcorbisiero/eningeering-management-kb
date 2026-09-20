---
title: Code Reviews
tags: [process, technique]
summary: Examines what code review has traditionally built — defect detection, knowledge transfer, and shared ownership — and how AI should augment rather than replace human judgment. Reach for it when designing AI-assisted review workflows or evaluating how to preserve the learning value of review.
related: [shifting-judgement-left]
---

# Code Reviews

### What did code reviews solve for?

- Finding defects
- How teams shared knowledge
- Build collective ownership
- Spread architectural understanding
- Taught junior engineers how experienced developers think

### What devs want from AI reviews

"Should be able to detect high risk changes and derisk them."

- catch security and compliance issues
- flag high-risk changes
- generate test scaffolding
- surface the impact of a change across the codebase
- handle the high-volume routine so human attention can go where it matters

### What devs *don't* want from AI reviews

"I don't want AI to just act as a red-light / green-light. It should raise issues… and still require human review."

- AI that auto-merges, auto-commits, or takes final accountability

### Thinking wisely

AI should make human review more valuable, not eleiminate it. AI-enabled review should have discipline around it:
- clear eligibility criteria
- thoughtful risk stratification
- deliberate decision about which changes deserve human attention, and why

The wrong question: "Does AI review work?"
The right questions:: "How does AI review maximize the time and value of human judgment?"

*If* you can completely automate the review of a diff, the effects:
- you haven't transferred any knowledge
- you haven't built shared ownership
- you haven't given a newer engineer a window into how a more experienced teammate reasons about trade-offs
- you haven't surfaced the design rationale that someone will need six months from now when they're trying to respond to customer feedback

### More than technical debt

- As AI accelerates software development, teams will accumulate cognitive and intent debt. This is a growing gap between what the system does and what the organization collectively understands about why it does it.
- These debts surface months later, during an outage, a handoff, or a redesign, when nobody remembers the reasoning that once lived inside a code review conversation
- At this point, recovering that understanding is far more expensive than preserving it would have been

### So now what?

We can try improving in 3 areas:

Three things, in order.

#### Fix the basics first

Audit your current review process:
- Are pull requests small enough to review meaningfully?
- Do change descriptions explain why, not just what?
- Are reviewers protected from overload?
- Are automated tools already handling the routine work they should (e.g. formatting, linting, and obvious style issues)?

#### Design AI around human judgment

- Developers consistently describe code review as high-value, high-accountability work which means they don't want AI making the decision but helping them make better ones
- AI should surface issues not solve them independently

#### Protect what review is actually building

- The easiest thing to measure about code review is defects
- The most valuable thing it produces is shared understanding
- Are junior developers learning?
- Is architectural knowledge spreading across the team?
- Are reviewers engaging with substance or simply rubber-stamping?

Tip: Design your AI review strategy so automation absorbs the routine while humans spend more time on the conversations that create understanding, ownership, and better engineering judgment.
