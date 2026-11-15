---
title: Engineering Strategy
tags: [strategy, framework]
summary: A framework for identifying and addressing high-stakes business problems from an engineering perspective — covering strategy vs. vision, diagnosing team and architecture problems, and structuring execution through coherent action.
related: [what-is-strategy, practicing-strategy, red-teaming-strategy]
---

# Engineering Strategy

## What is it

Engineering Strategy is how we address a High-Stakes Business Problem from the Engineering Perspective, which can be multiple things, like:

- The time to market for new features is high, such as six months of Go-To-Market.
- The company has to buy hardware in advance to supply customer needs, creating a bottleneck and being unable to serve our scalable needs on-demand.
- The pandemic hit, and our ceremonies, infrastructure, and ways to ship software are highly coupled to teams being in the same room.
- The mobile team grew by a lot, but they cannot ship with a good tempo, being unable to deliver on customer needs.

Those High-Stakes Business Problems can translate into engineering as:

- A Big Ball of Mud that doesn't allow us to move fast enough to serve our clients' needs.
- The need to move from on-demand hardware to the cloud.
- Creating the proper infrastructure, ceremonies, and support for the teams to work from home.
- The need to re-architect a mobile application to allow team growth while touching the same monolithic repository.

## Engineering Vision != Engineering Strategy

- Engineering Strategy is about a high-stakes business problem
- Engineering Vision addresses the whole Business Vision

Treat engineering vision as a guideline for people to make business-engineering aligned decisions daily so that we don't create many high-stakes situations.

## So a bad strategy is?

> Bad strategy is not simply the absence of good strategy. It grows out of specific misconceptions and leadership dysfunctions. -Richard Rumelt

Examples:

- Fluff. It uses buzzwords and apparently esoteric concepts to create the illusion of high-level thinking.
- Failure to face or recognize the challenge.
- Mistaking goals for Strategy. Being just a statement of desire rather than plans for overcoming obstacles
- Bad strategic objectives. When they fail to address critical issues or when they are impracticable.

## Understanding the high stake problem

### Starting from the business and product

What if the business is wrong?

- You all will learn from the situation and improve! That's why being hypothesis-driven is so essential. You start from an assumption instead of a fake fact.

As Technical Leaders, we need to be close to the business, listen to what product/business says, ask questions, be informed, and stay curious. Avoid making assumptions!

### Understand you cannot one-shot this

There may be friction and team barriers that slow you down.

#### Team communication

- Identify what is In and Out Communication, and which information flows between them
- Strong or weak dependency
- Which is the "distance" between teams that people feel

#### Team handover

Identify how the product is shipped to the customers and how many teams are involved in the progress. Those handovers can be damaging for our organization in preventing a fast flow of change.

## Direction and Coherent Action

- Clustering per topic or area
    - Do not discard an issue because it affects only one team, assess the implications of that risk
    - Choose the right size of the topic.
        - Bad: Java Unit Tests (too low) or Move to the Cloud (too high)
        - Good: Enhance our Testing Practices or Adopt the Cloud for on-promise instances for client-facing services.
- prioritize based on the business
- pick 2 or 3 areas to focus on as you will be more likely to fail if you don't put people's effort into a few things at a time

## Execution strategy

During an Execution, there are at least three actors:

- Who led the Engineering Strategy Design
- Coherent Action Lead
- Coherent Action Helper

Between them, you need to align the expectations of who will do what.

### Planning Expectations

- When will we hold a kick-off meeting to align the Coherent Action Expectations?
- How much effort will it require?

### Execution Expectations

- How much team time will we dedicate in each team sprint?
- When will we do checkpoints to see the progress?
- How many team members do we need for this coherent action?

### Reporting Expectations

- How will we report the progress?
- Who is responsible for making progress visible to everyone?

## Questions that can help identify the high-stakes problems

- What could prevent us from achieving the business goals?
- What are the current risks, both internal and external?
- What are the barriers that are impeding us from reaching our goals?
- Where do we have more friction?
- Where are the bottlenecks?
- How is Conway's Law affecting us?
- Is our communication optimized for a fast flow of change?
- Do we have close collaboration between domain experts and engineering to make knowledge available to all team members?
- Do we know our customers, their needs, and their journeys?
- Are we measuring outcomes? How do we know we are on track?
- Will our architecture support the next 2x growth?
- Can we recover from a disaster like an AWS region going down for several hours?
- What is the maturity of the service based on the [24 capabilities](https://itrevolution.com/articles/24-key-capabilities-to-drive-improvement-in-software-delivery/)?
- How are the teams performing based on the 4 key metrics of Accelerate?
- What are the interactions between teams?
- What are the value streams?
- What is the cognitive load of the teams?
