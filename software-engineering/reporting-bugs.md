---
title: How to Report a Bug So It Gets Fixed
tags: [process, technique]
summary: A practical checklist for writing bug reports that maximize the chance of resolution — covering verification, bisection, test-case minimization, and writing the report you'd want to receive. Reach for this when filing an issue against an open-source library or escalating a bug to another team.
related: []
---

### How to report a bug so it gets fixed

* Assume you are wrong meaning spend time actually determining if it is a real bug or not before claiming it to be a bug  
* Make it deterministic  
  * If something is random, it usually means you haven’t really found what the root of the issue is  
* Bisect versions e.g. git bisect  
  * Its like a binary search on where the bug was introduced  
* Shrink it into a public repository  
  * You might have private data or your code env might be super complex for someone else to replicate  
  * You want to help the owners of the bug by letting them easily replicate it with a sample example you used to verify the bug exists  
* Report it with evidence  
* Do the archaeology  
  * Check history, trackers etc to see if this was a recurring issue, known about, incorrectly fixed  
* Write the report you’d want to receive  
  * If you want your issue to be fixed quickly, you want to create a report that has a lot of information in it  
  * Including any history, reproduction steps, any information that is useful that the read might not know  
* Be as helpful as you can in the comment section of the issue  
* Verify the fix yourself, don't just assume it works