---
title: I Don't Want the Details
tags: [incidents, technique]
summary: Reframes incident postmortems from explaining what happened to identifying systemic changes that prevent recurrence. Reach for it when running a postmortem or coaching a team on how to make lasting improvements.
related: [developing-a-sixth-sense-for-the-long-term]
---

# I don't want the details

Imagine having a problem or outage, fixing it, and your boss says, "I don't want the details".

They continued:

I know that if we get into the details, the reasons will be perfectly reasonable. You'll explain what happened, I'll understand why everyone made the decisions they made, and I'll empathise with you. Then it'll happen again. So I don't want the details. I want to know what we're changing.

You might think this is being dismissive, but it is not. The person is actually saying, "I already believe you. Now let's talk about what happens next".

## Asking the right question

After something goes wrong, most organizations ask "Why did this happen?"

After an outage, you:
- write up timelines
- reconstruct decisions
- explain dependencies
- we hand over a document that contains the specific combination of events that led to the incident
- everyone nods their head, says "that makes sense"
- we all move on with our day

Then when the issue surfaces again 6 months later, everyone is left wondering how we landed here again.

So don't ask "why did this happen?". Ask, "What are we changing so that the same class of failure is less likely next time?"

## People

Assume reasonable people produced this outcome, so what needs to change?

Consider these examples:

Example 1
Problem: "We missed it because Alice was on holiday and Bob thought the Widgets team owned it".
Thinking: How do we make ownership unambiguous when someone is unavailable?

Example 2
Problem: "The requirements changed three days before launch."
Thinking: Of course they did! What happens when requirements change inside the launch window?

Example 3
Problem: "The alert fired, but the on-call engineer had already dealt with twenty low-value alerts that evening".
Thinking: Makes sense. How do we improve the signal to noise ratio of our alerts?

## Good explanation != Fixed

How many postmortems are full of sentences like:
- "we should involve support earlier"
- "we need to communicate better"
- "we'll be more careful next time"

If everyone involved in the incident left the company tomorrow, would the fix still work? If the answer is no, the system is still destined to fail.

For a postmortem to drive lasting change, ask, "If the same situation happened tomorrow, what would cause a different outcome?"
