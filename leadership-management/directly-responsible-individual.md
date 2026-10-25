---
title: Directly Responsible Individual
tags: [ownership, ai, framework]
summary: The DRI model assigns single-person accountability end-to-end for a project, including delivery, stakeholder communication, and trade-off decisions. Particularly relevant in AI-era orgs where agent-assisted solo ownership is becoming the norm and traditional management shielding is a liability.
related: [management-in-the-age-of-ai]
---

# Directly Responsible Individual

## A changing world
### Past
Every project had a product manager, an engineering manager, a tech lead, and a designer all working on clear pieces, the collaborative nature of the work meant that it was easier to see when something was slipping or getting blocked, and multiple humans would work together to remedy this.

### Evolving Now
- An increasingly agent-based, solo-owner way of working, projects, and the people that are doing them, are becoming isolated
- AI can generate status updates from tickets, but that can make it harder to read between the lines
- Add individual contributors who aren’t experienced at operating at this level before, and all of your projects can begin to drift off track without a close watch being given to them

So how do you maintain span of control but empower IC to do more?

## Project ownership
Note:
- To be clear, having DRIs doesn’t fix coordination or guarantee the outcome
- It makes it 100% clear who is responsible for getting it done, and 100% easy to talk to that person directly to ensure things are going well and are moving in the right direction
- A DRI is accountable for delivery end to end AND it is possible to have nested DRI's owning sub-projects

## Who is the DRI?
- DRIs should always be the IC doing the work
- DRI should have their hands on the keyboard and their head in the codebase
- When you ask a question to your DRI about any technical questions, your DRI should be able to show you the code and also change it if needed

- You may question if there are wasted cycles when all comms need to pass through multiple people (manager, product, design)
- Maybe the message is massaged or loses substance
- Truth-seeking conversations begin by engaging with the person who has the answers, and that person is typically the IC since they are closest to the action

- Stereotypical management practices like “shielding the team” are now being considered bugs that need to be fixed
- Individuals need to be coached into becoming more rounded engineers that can take full ownership of what they are working on, and have ample communication flow from it

## So what responsibility falls to engineers?
Being a DRI is an increase in the scope of what the job is.

Meaning:
- It means one person has to build the thing (maybe they do everything with AI, maybe they still need to delegate work out to other individuals helping them)
- Communicate with senior stakeholders
- Make the trade-off decisions that get it across the line

In a non-DRI model, the engineer usually handled the first while the engineering manager or product manager handled the other two.

Typically, a senior engineer should be able to take on a DRI role as it stands, albeit with a little practice. A more junior engineer will need coaching to grow into it. If you are going to implement this, it helps to bake the DRI responsibility into your levelling framework with clear responsibilities so that, for example, senior engineers know what is expected of them when they do it.

Being a DRI on projects is a fantastic stretch opportunity for non-senior engineers who want growth opportunities, and I find that it allows progression up the IC ladder to have additional paths rather than just becoming a machine that inputs lots of tickets and outputs lots of code.

If you are switching to a DRI culture, you’ll need to go through an initial period where you help coach everyone through the change. For example, a common one is some DRIs don’t expose enough information for others to understand what’s going on. The solution here is to find those that are doing it best and share repeatedly, loudly, and widely what good looks like, encoding those practices into processes and templates if needed. With time, everyone will get better.

The additional communication required is often the demand engineers are least experienced with. Many engineers, even senior ones, have never had to write (or generally share) the meaning and impact of their work regularly, as their manager or product manager would do this for the team instead. Surfacing the good and the bad of what they’re doing in public is new for a lot of people, so help them with it, and always interact and support them whenever there is annoying news being shared, like projects slipping.

The path to senior engineer is steeper in an organisation that runs on DRIs. However, this is something that I personally am happy with. I believe that it is an increasingly core skill where more of the programming work is being done with AI.

## What is needed from upper management
- Failure is ok as we try this out. It is new territory and some things might not work or go as expected. Retro those and improve
- Teams need to strike the right balance. Too many seniors (not growing the next generation), too many juniors (not enough tenured people to mentor)
- AI is not going to solve a mentorship role for now. Knowledge bases, agents, etc have always been regarded as ways to extend the skillset of a person, not replace them
- They need to explicitly define or re-define the roles of a tech leads, team leads, and managers

## You have this new org, now what?
Built a rhythm around the DRI model.

Example:
- Every DRI posts a written update in a shared note
- Leadership reads every update
- DRIs and leaders can book a standing office hours slot with each other


For updates: It doesn’t need to be elaborate; it needs to be accurate and consistent.

A good update covers:
- Current status, with dates and scope. On track, at risk, or off track, plus an explicit flag whenever the target date or the scope has moved since last time.
- Progress and what’s next. What has been done this week, and what the DRI is doing next in the coming week.
- Risks, blockers, and asks. What’s worrying them, what’s blocked, and what they need from others at this moment in time.
- A link to the work itself. A demo, a pull request, or a staging link, so the reader can look or use the real thing if possible.

**AI can now draft much of this from the project state, so the writing takes less time. The important bit is that the DRI writes it and you read it.**

You may have something like 30 projects running at any one time. Whether it is you or some automated process, you need to nudge the DRIs to post. Reading the updates should take anywhere between 30-60 minutes depending on how much detail people have gone into. There will be some projects you want to be extremely close to and that is where office hours/weekly comes into play.

These generate pulls and pushes. A pull is where leadership want to know more, and a push is where a DRI needs explicit help.

Example pull (leadership -> DRI) when:
- A project is blocked for reasons outside of their control
- You don’t understand the content of their update (this is a good coaching moment)
- You disagree with something (e.g. direction, technical decision, etc.)

Different way to exercise this:
- The entirety of a single day can be reserved for office hours with leadership/product
- Encourage DRIs to come to us with anything, no matter how small. Booking a slot doesn’t mean that something has gone wrong. It could be anything from:
    - Working through a two-way door decision
    - Looking at different designs and trying to choose one
    - Helping decide which scope is in or out of the project
    - Showing us a demo to get feedback
    - Or just having a chat

**Key Point**
Ideally, leaders should book meetings with their DRIs as readily as DRIs book them in return. The model should be a trusted two-way collaboration over time, rather than a one-directional summons. 

**FY** When you start the DRI model, there may be lots of big interventions as many snags in projects worked their way to the surface. Over time, and with more direct communication between leaders and DRIs, there is little left hiding.