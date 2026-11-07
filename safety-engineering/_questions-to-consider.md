---
title: Safety Engineering — Questions to Consider
tags: [incidents, technique]
summary: Self-reflection prompts for examining the blind spots, untested assumptions, and false confidence that accumulate in systems and teams over time.
related: []
---

# Safety Engineering — Questions to Consider

Use these questions when exploring the notes in this folder. They are not meant to be answered all at once — pick one or two that create friction.

## Hidden risk

- What failure mode am I most likely to miss because I'm too close to the system?
- Which "it's never happened before" risks am I treating as though they can't happen?
- Where is my team relying on alerting that has never actually caught a real incident?

## Incident readiness

- If our most critical service failed in the next hour, how confident am I in our runbooks?
- What assumptions is our system making about external dependencies that haven't been tested under failure?
- When did someone last run a drill or chaos experiment — and what did it surface?

## Learning from incidents

- After our last incident, what did we fix that was cosmetic — and what actually changed the risk profile?
- Are postmortems on my team generating systemic improvements or just lists of action items that fade?
- What incident are we one bad day away from that everyone knows about but hasn't been prioritized?
