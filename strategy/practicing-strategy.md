---
title: How to Get Good at Strategy
tags: [strategy, technique]
summary: A collection of diagnostic questions, red-teaming prompts, and self-assessment checks for developing and stress-testing strategy, plus a framework for connecting mission, vision, strategy, goals, and metrics.
related: [red-teaming-strategy, what-is-strategy]
---

# How to Get Good at Strategy

## Questions to Consider

- *"What is the true, critical challenge here that we're looking to solve?"*
- *"What information or scenario have I been avoiding?"*
- *"What's the one thing I don't want to think about that I should probably think about?"*
- *"Anything I've found myself glossing over, postponing, or ignoring altogether?"*
- *"What's something others are overlooking?"*
- *"Why hasn't this been done before?"*
- *"What would have to be true?"*
- *"How can I keep things simple?"*
- *"What am I / what are we saying 'no' to?"*
- *Did you get the hard facts right? The strategy can't just be "we are going to build this and this." Have you identified the hard facts to show that doing those things would lead to material benefits?*
- *Do you have the credibility to implement the strategy? Do people trust you? Have you already earned the stripes?*
- *Is there commitment behind the strategy? Do you know who the stakeholders are, and whether they agree with and are willing to defend the strategy's objectives? The commitment needs to be deeper than lip service. You want people to be excited about the strategy.*
- *Is the timing right? Are the conditions suitable for change? If not, should you wait?*
- *Do you have the right alliances to implement the strategy? Who all needs to work on the implementation? What's in it for them?*
- *Do you have the right people to execute the strategy? Do they have the skills?*
- *How do you propose to manage change? Strategy may require people to let go of existing ways of doing things, and you may face resistance to change. How do you propose to address such resistance?*
- *Do you have the proper organizational structure to support the strategy?*
- *How will people make decisions during strategy implementation? Who decides? Who provides inputs? Who is accountable for what?*
- *How will you make tradeoffs and manage risks? What are the guiding principles?*
- *Do you have quantitative or qualitative ways of measuring progress?*
- *What processes are required to manage the implementation? Processes help catch blockers early and rebuild necessary alignment as things change.*

## Spending Effort

- Once you start defining projects, focus on the ones that serve multiple strategies at once
- Example: Say the sales team manually emails orders to the delivery team. You could replace that with an API connection. That alone cuts labor costs. But there's a second win: if you're also planning Project X, and it needs real-time order data, that API suddenly becomes critical infrastructure. One move, two wins.
- Maybe the first time you don't get taken seriously, but the second time you have a higher chance to be in the conversation
- Suggesting projects doesn't mean you're committed to them, it means you're helping shape the conversation

## Mission

- Why does the company/team exist? What problem(s) are we solving?
- Mission is timeless

## Vision

- The image of what that solution looks like in X years. There are different visions at different time intervals.

## Strategy

- How is the org/team going to accomplish the mission?

## Goals

- What outcomes must be accomplished to prove the strategy is working?
- Goals are time-bound

## Metrics

- Which numbers measure how close the org is to those outcomes, and by how much?
- Some missions don't have metrics that trace cleanly to mission, strategy, goal because these upper layers weren't written with enough specificity to be measured.

## Simple Example

- Our Mission: Reduce the cost of running Block
- Our Top-line Metric: \$ saved measured as:
  - Operations tooling: direct calculation of employee time saved, translated into dollars.
  - Safety and trust: dollars of fines and losses prevented.
  - Machine learning: projected savings from model improvements, reported with a confidence interval. ML work is inherently experimental: a project either wins big or returns nothing, so comparing it head-to-head against deterministic teams is unfair without a range around the estimate.

## Bad Example

- If the goal is "grow the business," someone has to define what growth means for the business.
- If the strategy is "win by being the best at X," someone has to define what "best" is.

## Three Types of Metrics

- **Target** numbers a team is actively trying to move. Every target traces upward to a strategy and goal.
  - Examples: revenue, active users, gross margin.
- **Guardrail** a counter-metric paired with a target, to catch damage done chasing the target.
  - Examples: customer retention paired with revenue growth; uptime paired with feature velocity; CS escalation rate paired with product change velocity.
- **Diagnostic** numbers that explain movement in targets or guardrails. A diagnostic tells you why, not whether.
  - Examples: funnel step conversion rates, cohort breakdowns, per-segment retention.
- Common failure
  - someone sees a diagnostic in a dashboard and sets a team goal against it
  - Now the team is optimizing a metric that was never meant to be moved, and the cascade drifts
  - Categorize every metric before it enters a plan.

## What Benefits Does a Mission, Vision, Strategy Give You?

- Clarifies the actual problems the team is trying to solve
- Unifies the internal team and motivates everyone to advance towards a shared future
- Helps partner teams understand the value of building on top of a platform vs building things individually.
- Clarifying the contract between the two partnering teams forms a healthy working relationship and thereby improving cross-team communication and collaboration.

## Example Using LinkedIn:

- **Problem**: Professional individuals need a way to connect and network with other individuals to look for new opportunities, hire great talent, further their careers by meeting like minded people, all around the world.
- **Mission** is to be the platform that connects career professionals and gives them the ability to accomplish their professional needs.
- Broker across teams, it can look like:
  - Messaging's mission could be something like: create a messaging platform that makes sending and receiving messages from other professionals easy and effective.
  - Profile's mission could be: Allow professionals to showcase their resume in a short and concise way: easy to update and easy to consume.
