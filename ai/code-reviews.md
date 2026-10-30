---
title: Code Reviews
tags: [ai, technique]
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
- Compliance reasons

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

AI should make human review more valuable, not eliminate it. AI-enabled review should have discipline around it:
- clear eligibility criteria
- thoughtful risk stratification
- deliberate decision about which changes deserve human attention, and why

The wrong question: "Does AI review work?"
The right questions: "How does AI review maximize the time and value of human judgment?"

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

#### What to avoid
"Meat proxy" - using AI to leave comments, human walks through to vet the comments, and then has AI review said comments. It becomes an unnecessary bottleneck.

## Examples in the wild

### `small-change`

When a pull request is marked ready, CICD determines whether it is eligible to be a small-change. 

1. Something is a small-change if it meets all of these criteria:
- It is less than 1,000 lines of code
- There are no p1 or p2 findings from our ai-code-review automated review bot
- The author has “experience” in the service or application, defined as 10+ prior merged pull requests into that service or application’s directories. For changes working across multiple services or applications, the author must have experience in all of them to qualify
- Impacts fewer than N distinct services or applications. N is 1 on our frontend monorepo, and N is 3 in our backend monorepo, where typical changes will modify both a gRPC service and a common HTTP gateway
- Shared libraries and utilities files are not eligible for small-change
- Each repository has a .small_change file which allows per-path customization while we continue to tune the behaviors. For example, a service dealing with money movement can be excluded
2. Our Slack automation tags every reference to a pull request with reacji labeling the state of that pull request, for example if it has failing tests, if it has been approved but tests are still running, or if it is ready to merge. We added a small-change reacji that indicates which of those pull requests meet the small-change criteria
3. In our internal skills repository, we created two skills that have been distributed across harnesses:
- review-small-change which takes a list of repositories and reviews all open, non-draft, small-changes, including providing approval if they meet the review’s criteria (all checks pass including small-change check, and not touching on sensitive topics such as payments and security).
- review-pr-cluster which reviews batches of pull requests to identify common themes that came up, and suggest opportunities for discussion and adding verifications
4. We set the social expectation that any error caused by a small-change is a failure in our system, and has to be solved at the system level: improvements to ai-code-review, to our verification mechanisms, to our CICD, to our harness, etc.