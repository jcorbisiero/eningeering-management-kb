---
title: Building Feedback Loops
tags: [ai, technique]
summary: Three techniques for capturing agent intent and observing AI systems at runtime — requiring tool call rationales, building a structured feedback tool for blocked agents, and adding purpose-built parameters to individual tools.
related: [supervisory-engineering]
---

# Building Feedback Loops

- Require a 'rationale' on every tool call. Every MCP or CLI tool call requires the agent to include a rationale parameter explaining why it's making the request. We can't see the chat, but the rationale reconstructs intent. Patterns in the rationales tell us what people are actually trying to do.
- A feedback tool. Build a standalone tool the agent can call when it gets blocked or runs into a pattern that isn't working. The agent submits what it was trying to do, what it tried, and where it got stuck.
- Tool-specific seeds. Add in purpose-built parameters to individual tools to capture context we'd want later: things the agent has access to that we'd otherwise have to infer.

## Different ways to get feedback
1. Observability

Invest heavily in observability, both black-box and white-box, and make sure to keep a direct handle on the metrics instead of solely relying on the agents’ view. As a habit I prefer to triangulate onto a behavior with multiple sources of metrics, and that becomes even more important with systems rapidly becoming opaque.

2. Non-functional requirements

Observe resource utilization and other non-functional requirements: these can be canaries for unexpected behavior.

3. Deterministic validation

Build mechanical straitjackets for the model: have held-out pieces of code or deterministic tools for validation and observations as a hold-out against the model misunderstanding or glitching.

4. Shadow Traffic

Make it possible and cheap to run a deployed candidate against shadow traffic with no side effects: keep it as similar to production as possible, and this can be the final gate to prevent surprises.

5. Style guides

Give the model a style guide based on your existing code and work.

6. Fast deploys

If you can’t be sure of quality, make it very easy to deploy code as well so changes can be shipped and reverted extremely rapidly.
