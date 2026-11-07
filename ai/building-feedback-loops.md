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
