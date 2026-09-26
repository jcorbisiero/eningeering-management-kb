---
title: Shifting Judgement Left
tags: [ai, technique]
summary: Argues for moving knowledge-sharing, design alignment, and quality enforcement earlier in the development workflow — through pairing, mob programming, and automated checks — rather than relying on code review after the fact. Reach for it when evaluating what value code review is actually capturing versus what earlier practices could achieve instead.
related: [code-reviews]
---

# Shifting Judgement Left

- If we want to explore alternative solutions, do that before implementing one of them.

- If we want knowledge transfer, pair. Sitting next to someone, physically or virtually, while they reason through a problem teaches you far more than reading their completed solution afterwards.

- If we want junior engineers to learn how experienced engineers think, let them work with experienced engineers while they're thinking. Pairing comes to mind again here, but teams could also do design sessions collectively with a whiteboard before they write (or instruct the agent to write) anything.

- If we want collective ownership, organise teams so people actually build and operate software collectively rather than relying on a pull request to tell everyone what somebody else has already built. Use pairing, mob programming, or team design sessions around whiteboard.

- If we want architectural alignment, design together and then encode the important constraints as fitness functions.

- If we're reviewing code for formatting, linting, known security problems or things that can be deterministically tested, automate them.
