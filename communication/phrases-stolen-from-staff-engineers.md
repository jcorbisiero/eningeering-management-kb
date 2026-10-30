---
title: Phrases Stolen from Staff Engineers
tags: [communication, technique]
summary: Seven high-leverage phrases staff engineers use in meetings — each names the conversational move it makes and when to use it. Reach for it before a tricky meeting or when a discussion is drifting.
related: [ask-more-questions]
---

# Phrases Stolen from Staff Engineers

1. "What problem are we actually solving?"
The move: forcing scope.

When people in the room cannot agree on the answer or scope, that disagreement is the actual information. You have just surfaced, in one sentence, the thing that was going to make the meeting fail in forty minutes anyway. Now you get to fail in two minutes instead, and reconvene with the right people.

2. "What does done look like?"
The move: forcing definition.

This one is unglamorous and I cannot overstate how much it changes things. Most projects in tech are running without a clear definition of done, which is why they sprawl, why deadlines slip, and why the retro is full of confused energy about what was supposed to happen.

Asked at the start of a project, this phrase forces the team to write down the smallest concrete artefact that would constitute completion. A demo. A merged PR. A document. A specific number on a specific dashboard. Asked midway through a project, it is even more useful, because it surfaces the gap between what people think they are building and what they have actually agreed to build, which is usually substantial.

3. "What would change your mind?"
The move: forcing rigour.

**Most Dangerous** because if you ask it of someone whose mind is genuinely closed, you will get a hostile response. Use carefully.

It takes a disagreement that is sliding into trench warfare and converts it back into a question. If two people in a meeting are stuck on opposing positions, asking either of them what would change your mind forces them to specify the conditions under which their position would be wrong. If they can name those conditions, you now have something testable. If they cannot, you have politely surfaced that the disagreement is not actually about the technical question, it is about something else, and you can stop pretending otherwise.

4. "Who is the decision-maker on this?"
The move: forcing accountability.

There is a recurring pattern in tech meetings where six people debate a thing for an hour and then disperse without anyone deciding anything, and the next meeting on the same topic, a week later, contains seven slightly different people and starts from scratch. This phrase, asked early, kills that pattern.

It just asks the question that has, somehow, gone unasked, and forces the answer to be a single name.

- Sometimes the answer is "actually, that's me," delivered slightly sheepishly
- Sometimes it is "we need to loop in so-and-so."

A variation I use when the meeting is already underway and going in circles: who needs to be in the room for us to actually close this? Same move, slightly softer landing.

5. "What is the cheapest version of this we could ship?"
The move: forcing tradeoffs.

Engineering teams default to building the complete, correct version of a thing. This is one of the great strengths of the discipline and also one of its great failure modes, because the complete, correct version usually takes four times as long as anyone estimated, and ships into a world that has already moved on.

This phrase makes the team articulate, out loud, what could be cut. Not what should be cut but what could be. Almost every engineer has private opinions about which parts of the spec are overbuilt, but the social cost of saying so unprompted is high, because it can sound like laziness or like criticism of whoever wrote the spec. Asking the question explicitly gives everyone permission to surface those opinions without owning them.

Avoid the term "MVP" because MVP has been so worn down by overuse that it now means whatever the listener wants it to mean. The cheapest version we could ship is harder to wriggle out of.

6. "What are we assuming that might not be true?"
The move: forcing surfacing.

Most project failures in my experience trace back not to bad decisions but to unexamined assumptions. The team assumed the API would be ready. The team assumed the data would be clean. The team assumed leadership cared about the same outcome the team cared about. Each of these assumptions, written down on day one, would have been recognisable as a risk. Left unsaid, they each became the reason something fell over in week six.

This phrase is most useful in planning meetings, but I have also used it in incident reviews, where it does a slightly different job: it asks what we thought was true that turned out not to be. Same move, different timeframe.

The thing to watch for is the silence after you ask it. If the room is silent for more than a beat or two, the room does not actually have an answer, which is itself the answer. There are always assumptions. If your team cannot name any, they have not been looking.

7. "I might be missing something, can you walk me through it?"
The move: forcing teaching.

It forces the person who is talking to slow down and explain their reasoning step by step. Most of the time, this explanation reveals that the person talking has not actually thought through the thing they are confidently asserting. Occasionally it reveals that they have, and you learn something useful. Either outcome is better than nodding along.
