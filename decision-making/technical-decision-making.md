---
title: Technical Decision Making with RFCs and ADRs
tags: [decision-making, architecture, framework]
summary: Step-by-step guide for making technical decisions — writing the RFC with priorities over pros/cons, running async review, holding a structured decision meeting, and recording the outcome as an ADR.
related: [decision-making-techniques, key-person-risk]
---

### Technical Decision Making RFC/ADR

Step 1 \- Write the RFC

* Listing the priorities is more important than a list of pros/cons because people will focus on the wrong thing  
  * Priorities set the constraints that the change must abide by  
  * So when people disagree, you’re debating what actually matters, not arguing over vague trade-offs  
* Tag the right people  
  * Will be affected by the decision (they need to know)  
  * Has relevant expertise (they can improve the decision)  
  * Has authority over the affected area (they need to approve)  
  * Will implement it (they’ll spot practical issues)  
* Rollout plan  
  * Need a clear path from current state to the desired outcome  
  * Many architecture decisions fail not because the decision was wrong, but because the implementation path was unclear or too ambitious  
  * People push back on “massive paradigm shifts” not because they disagree with the direction, but because they can’t see how to get there incrementally

Step 2 \- Async Review Period

* Encourage people to:  
  * Ask clarifying questions — “How would this handle X scenario?”  
  * Raise concerns — “This might conflict with Y initiative”  
  * Provide additional context — “We tried something similar before and hit Z issue”  
  * Express preferences — “I lean toward Option B because…”  
  * Suggest alternatives — “Have we considered W approach?”  
* What if no one comments?  
  * The decision isn’t important enough — Maybe this doesn’t need a formal process. Just decide.  
  * People are too busy — Ping individuals directly. “Hey, I really need your input on Section 3.”  
  * It’s too long/complex — Simplify. Add a TL;DR at the top.  
  * People agree but are silent — Explicitly ask for “+1 if you’re okay with the recommendation”

Step 3 \- Decision Meeting

* Duration: 30–60 minutes (not more)  
* Agenda:  
  * Quick context (2 min) — “We’re here to decide X. Everyone’s read the RFC”.  
  * Address open questions (10–15 min) — Go through unresolved comments and open questions from the RFC  
  * Discussion (15–30 min) — Debate the options, raise new concerns  
  * Decision (5–10 min) — Make the call  
* Who should be there:  
  * The RFC author (runs the meeting)  
  * Key stakeholders who commented  
  * The decision maker (if that’s not you)  
* Decision-Making Methods  
  * Consensus: Everyone agrees. Ideal but not always realistic.  
  * Consent: Nobody has strong objections. Different from consensus — you’re asking “can you live with this?” not “is this your favorite?”  
  * RAPID/DRI: One person (the Directly Responsible Individual) makes the final call after hearing input. This is often best for architecture decisions where someone needs to own the outcome.  
  * Voting: Can work for minor decisions but tends to create winners and losers. Use sparingly.  
* What If You Can’t Agree?  
  * Escalate: If there’s a clear owner or manager above the group, they can break the tie. This isn’t a failure — it’s what leadership is for.  
  * Time-box: “Let’s try Option A for 3 months and revisit.” Not everything needs to be decided forever.  
  * Do more research: If the disagreement is factual (“will this scale?”), maybe you need a spike or proof of concept before deciding.  
  * Smaller scope: Sometimes you can agree on a subset. “We disagree on the long-term approach, but we agree on the first step.”  
  * Acknowledge trade-offs: Sometimes people disagree because they’re weighing trade-offs differently. Make those explicit. “You’re prioritizing speed, I’m prioritizing maintainability. Let’s figure out which matters more for this specific situation.”

Step 4 \- Writing the ADR

* When Stakeholders Need to Be Involved  
  * Just decide (no RFC needed):  
    * Affects only your team  
    * Easily reversible  
    * Low cost to change later  
    * Lightweight RFC (async only, maybe no meeting):  
  * Affects 2–3 teams  
    * Medium impact  
    * Someone might have concerns  
  * Full process (RFC \+ meeting \+ stakeholders):  
    * Cross-cutting concerns (security, performance, cost)  
    * Hard to reverse (database choices, API contracts)  
    * Significant investment  
    * Requires budget or headcount  
  * Executive involvement:  
    * Affects company strategy  
    * Large budget implications  
    * External vendor commitments  
    * Compliance or legal implications