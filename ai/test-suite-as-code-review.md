---
title: Test Suite as Code Review
tags: [architecture, technique]
summary: Explores splitting codebases into smaller repos so AI agents can reason over bounded contexts more effectively, with analysis of the coordination and reliability trade-offs this introduces.
related: [code-reviews]
---

# Test Suite as Code Review

- Concept of moving slice of code into their own repos so that it becomes a smaller chunk of code agents can reason and enhance to address the context problem
- You can have a monorepo or larger repo but it costs more to set up rules to guide the agents and requires re-running the entire test suite (including code you did not touch)
- Splitting only works if the interfaces are well defined and there is a contract between repos

## Trade offs

- Features that used to be one pull request in the monorepo are now a change spread across several repositories
- Splitting a monorepo trades one kind of difficulty for another.
  - The first cost is in your own head. You have to decide which service a piece of work belongs in before starting it
  - The second cost is reliability. Repositories that used to fail together as one deployable now fail independently
  - The third cost is coordination that never goes away. Shared libraries need update schedules, API contracts need versioning, and a change that used to be one pull request can turn into three, timed so none of them ships broken.
- In a small repository, a feature can go from an idea to running in the product in about half an hour, and the only thing that half hour depends on is CI. In the monorepo, the same feature waited on tests for code it never touched.
