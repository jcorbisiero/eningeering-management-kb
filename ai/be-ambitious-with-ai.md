---
title: Being Ambitious with AI
tags: [ai, technique]
summary: Four lenses for raising ambition with AI — Altitude (outcome-level thinking), Depth (expert-level tools and methods), and Range (cross-discipline perspectives) — with concrete prompting techniques. Reach for this when you want to extract more than task speed from AI assistance.
related: [ai-speed-judgement]
---

# Being Ambitious with AI

Ambition can come in four domains: Speed, Altitude, Depth, and Range.

1. Speed

Essentially the same work in less time which is well established and requires little creativity in how you approach AI, so we will skip this one.

2. Altitude

Going up in abstraction and considering the outcome rather than the individual task.

3. Depth

Considering a task the way a field-leading expert would. Rather than operating at the task's layer, we go one level deeper and touch the underlying data, tools, and problems.

4. Range

Drawing on multiple fields rather than just the one the task might need at the surface, using knowledge, tools, and techniques you normally wouldn't.

## Altitude

- Ask yourself what do you want to happen next? What's the goal beyond the goal?
- A good tell-tale sign that ambition in altitude is a good idea is if you're going to have meetings to discuss whatever you're working on
- Doing this well often involves changing your workflow

Example: In order to let Claude make sure our app is crash-free, you may need to make sure it can easily fetch crash reports, understand which app version maps to what git commit, and give it access to Windows, macOS, and Linux computers so it can actually independently reproduce and verify fixes.

## Depth

Being ambitious in depth means pushing the model to use the tools, techniques, media, and knowledge employed by the best professionals in the field.

Consider a mix of the following useful techniques:

1. Insist on the same instruments used by the best in the industry
  - When prompted to act like a professional, models often switch vocabulary without actually switching methods
  - For example if you need same tools as the best data scientists and statisticians, insist on Claude using databases and statistical models, not md files

2. Pick unreasonable goals and tell the model that they're very reasonable
  - You need your website to load in 5s instead of 10s? Ask for 200ms. Does something seem impossible to the model? Reiterate that it's very much solvable, it just needs to keep going.

3. Challenge what you know
  - Give the model access to the raw information and data and ask it to adversarially check assumptions. "We believe churn is an onboarding problem. Try to reproduce that from the raw data."

4. Produce new knowledge
  - Ask Claude to find blind spots
  - For example, "Build a simulation of our customers that reproduces the last year from our logs. Then find the earliest signal of churn we don't know about yet, and show it predicts on data it has not seen."

5. Use an outside judge
  - Do not ask the model to judge itself
  - Ideally use a tool the model can run to get feedback immediately

A simple prompt that can help me:

> I want a deeper version of this task, not a bigger one. Before rewriting it: (1) say what a top professional in this field would do here that I'm not asking for; (2) name the rawest material they would start from instead of what has already been digested for me; (3) name the specific methods and tools they would use; (4) say what, other than you or me, would show the result is right. Then rewrite my prompt to ask for exactly that.

## Range

Being ambitious in range means that we consider our work from the perspective of different fields.

1. Try to replace the nouns with verbs
  - An old trick from The Art of Innovation by Tom Kelley and Jonathan Littman
  - For example, a quarterly review isn't "a deck". It's "getting busy people to believe a story about cause and effect, and to decide under uncertainty, in 30 minutes"

2. Assemble the crew
  - For example, you may need to bring in an analyst, a journalist, and an editor. If it has to be presented, probably a motion and audio designer, too. It might be useful to employ an adversarial "red team", too, so let's bring in a short seller and a forensic accountant.
  - Do not use this to adjust the transcript or content. Use this method to find fields and techniques. Don't ask the model to write like a short seller, ask it to do what a short seller does to research their position.
