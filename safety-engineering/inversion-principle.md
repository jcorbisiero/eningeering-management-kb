---
title: Inversion Principle for Project Safety
tags: [incidents, technique]
summary: A set of adversarial questions organized by failure mode — catastrophic failure, silent degradation, rollback, load, dependency failures, human error, and data integrity — to surface unknown unknowns before a project ships.
related: []
---

### Inversion Principle

Questions to consider when working on projects to catch unknown unknowns

* Catastrophic failure  
  * What would make this an absolute disaster?  
  * If this was to cause a Sev1 incident, what could some of the likely root causes be?   
  * What kind of scenario would have happened in order for that to trigger?   
  * Which single component failure would cascade most dramatically?  
* Silent degradation  
  * How could this fail without us knowing?  
  * What metrics are we not monitoring that we should be?  
  * Which failure modes wouldn’t trigger our existing alerts?  
  * Where might we have blind spots in our observability and logging?  
  * What could degrade slowly enough that we wouldn’t notice until customers complained?  
* Rollback  
  * What if we need to roll this back at 3am?  
  * Can this change be reversed?  
  * How long would rollback take?  
  * Is there anything that’s irreversible?  
  * At what point does rolling back become more dangerous than rolling forward?  
  * What happens if none of this works?  
* Load and scale  
  * What happens when real load exceeds our assumptions?  
  * If you’ve currently estimated a certain load, what would break at 10x that load?  
  * Are there any resources that you have assumed will work properly that could go wrong?   
  * What kind of behavior exists in high traffic scenarios with extreme contention or queuing?  
* Dependency failures  
  * What if everything that we depend on breaks?  
  * List out all of the external services that you rely on, such as databases and APIs. For each of them, think about what could go wrong if they became slow or unavailable.   
  * Think about whether you should have retries or circuit breakers.  
* Human error  
  * How could we break this ourselves?  
  * Are there any operational steps that could be prone to human error?  
  * Do we have everything written down in playbooks in case whoever is on call doesn’t understand what to do, or are we missing documentation?  
* Data integrity and security  
  * Is it possible for us to corrupt or lose data?  
  * Have we thought about race conditions that could happen? Or have we assumed transactionality that doesn’t actually exist?   
  * What happens if we process the same event twice, or if we skip one event?   
  * How do we know if data becomes inconsistent?  
  * Are there any attack vectors that we need to think about?  
  * Which data are we exposing and to whom?