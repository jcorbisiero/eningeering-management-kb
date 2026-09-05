---
title: Decision Making Antipatterns — Real-World Examples
tags: [decision-making, example, communication]
summary: Three concrete antipatterns and better alternatives — letting calendar availability set timelines, waiting for perfect information before sharing, and relinquishing control without follow-through.
related: [decision-making-techniques, technique-decision-making]
---

### Real-world examples

Bug \#1: Letting free calendar slots decide your timeline

* Scenario  
  * In order to make a decision, you find the list of people that need to be involved in order to reach consensus. You find a free slot some N days into the future.  
  * APPT has notes about your project and a short document with some notes outlining some different approaches you’d like to discuss and that you want help picking one  
  * Days pass w/o a response. You’ve just allowed arbitrary availability in everyone’s schedule decide that your work is going to take another nine days. When you think about it that way, it’s a bit preposterous.  
* Alternative universe  
  * After booking the meeting and attaching your notes to the agenda, you send a message to the group outlining what your project is trying to achieve and that there are several ways to do it.  
  * You enumerate the approaches in the message and highlight that you think that the second option is the most reasonable. You also say that you’ve reserved a meeting slot in the future if it needs some further debate. However, within 24 hours, all of the people in the group have replied asynchronously to say that they agree that the second option is the most viable, and they’re supportive of your team putting a prototype together. The meeting isn’t needed, and it gets cancelled. You then start building the prototype.

Bug \#2: Being afraid of sharing anything other than perfection

* Scenario  
  * Your approach to a project has several advantages and disadvantages around speed, eventual consistency and access patterns.  
  * Given that your team is producing a feature that others are going to use, you spend days putting together a document containing everything that the prototype has helped you learn so far, flow diagrams, sample code, etc  
  * Then you sit and wait for the comments. Thirty minutes later, you see a message come through from one of the engineers. It says “we’ve got internal libraries that already handle this problem for you”, and they send you a link to the GitHub repository and the documentation.   
  * You’ve spent a week trying to solve a problem that’s already been solved. What a waste of time.  
* Alternate universe  
  * After realising during the prototype that there were multiple ways in which data could be served from your feature, you decide to ask the teams that are going to use it for their input. One of the engineers replies. “We’ve got internal libraries that already handle that for you, have a look,” and they send you a link to the GitHub repository and the documentation.   
  * You use that library and finish the prototype more quickly than you thought you would. It’s still only Monday afternoon.

Bug \#3: Relinquishing control into the ether

* Scenario  
  * You’ve been working on hardening up your prototype so that you can deploy it into production for some initial testing with the other teams. You send in a PR and CI greenlights it.  
  * You find yourself repeating standup after standup, that you’ve finished the work, but you’re just waiting for someone to review it.   
  * You’re a bit puzzled by the response. “I’m still waiting for reviews, and it’s been three days,” you say. “Why didn’t you tell us?” they reply. “We’ll look at it now.” One hour later, and after a few comments, it’s merged and deployed.  
* Alternate universe  
  * After submitting PR, you send a message to the teams that are going to use your service to say that it’s available for them to look at. You ask that if they’ve got any time, you’d appreciate some eyes on it. “Sure,” one of the engineers says. “I’ll check it out shortly after I’ve finished this deploy.” One hour later, and after a few comments, it’s merged and deployed.