---
layout: post
title: Scrum and XP from the Trenches
excerpt_separator:  <!--more-->
comments: true
tags: ['Book Review', 'Scrum', 'Teamwork']
---

Reflections from rereading [Henrik Knibergs](https://www.crisp.se/konsulter/henrik-kniberg) book [Scrum and XP from the Trenches](https://www.crisp.se/bocker-och-produkter/scrum-and-xp-from-the-trenches) with five more years of work life experience than I had last time I read it, and now from a Product Owner perspective rather than a developer perspective.

A quick video summary of the Product Owner role (worth watching by itself) can also be found on Youtube:

<iframe width="560" height="315" src="https://www.youtube.com/embed/502ILHjX9EE?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

**TLDR:** Definitely worthwhile, reminded me of some things that has fallen to the side over the years of practicing (missing the forest for all the trees), and gave me some new ideas as well.

<!--more-->

## First things's first
Start at the beginning.
- Customer need/vision for how to solve it
- user-story mapping, impact mapping etc.

## Tools
Doing planning physically with index cards and post-it notes makes a lot of sense to avoid starting to adapt your process to the tool you are using, in my experience usually Jira.

The reason why this resonates with me is because I feel that Jiras technical nature and ton of fields, issue types and workflow settings tends to encourage people to lose focus on the actual user value. The Product Owner as the Jira administrator pattern is also all too common in companies where the PO lacks actual ownership over the product, and is in practice just a ticket monkey translating decisions made on another level into a Jira backlog.

Additionally, with my background as a developer I'm aware of the risk that I lose focus on on the bigger picture because I become part of breaking up user stories into technical subtasks, or spend time trying to configure the workflows to remove the sometimes arbitrary limitations that are set. In the end, it's about back to the basics;

> Individuals and interactions over processes and tools
(Agile Manifesto)

A suggested alternative to Jira (besides physical, which should be step 1) as well that I'm interested in trying is to handle the backlog entirely in Google spreadsheets. This gives complete flexibility in what fields to use for a story (though usually simplicity is best), and it's easy to reorder rows according to priority. Lastly, I except this to mean a shorter list that is more up to date compared to a Jira backlog that usually over time fills up with various technical tasks and other stories that never get prioritized.

In previous companies, I have worked similarly with high level stories in Google Spreadsheets for syncing progress with other Product Owners, which definitely helped keeping the 'bigger picture' in mind over looking at a Jira board.

## Before sprint planning
Just make sure there is a prioritized backlog available, and as product owner that you understand the why's enough to clarify them to the team as needed.

> Working software over comprehensive documentation
(Agile Manifesto)

This applies to planning as well, iteratively uncover the solution rather than planning it in too much detail before getting starting on implementation...

Regarding estimates;
> The important thing is not to get the absolute estimates correct (i.e. that a two-point story should take two days), the important thing is to get the relative estimates correct (i.e. that a two-point story should require about half as much work as a four-point story).

This of course as it's the effort combined with the value that will help organizing the backlogs relative priority.

### Scope, importance, estimate
These three variables are tightly coupled and describes the user story. The scope and importance are set by the product owner, whereas the estimate is given by the team based on the former. These three variables are fine-tuned through dialog between the product owner and team. Optimally, this is done to a large extent before the sprint planning in a separate meeting (backlog refinement), or continuously throughout the sprint for future stories.

## Sprint planning
Given that the backlog is in order and team and product owner have a clear idea of the customer needs and a vision for how to solve them, this meeting should be relatively straight forward. _If the meeting is not, then the issue is likely more in the previous stages rather than in how the meeting itself is handled._

That is also the reason why the length of the planning should be time boxed. If the planning takes more than a few hours, then the team has problems that you won't be able to solve in the planning. Better to start the sprint with a good-enough plan, and then focus on improving the backlog throughout the sprint so that the next sprint planning will run smoother.

In order to provide a clear scope for the stories, _the acceptance criteria should contain a clear description of how the story should be demo:d, as if it can't be demo:d, how do you know it's completed?_

### Sprint Goals
Similar to how a tool like Jira can end up causing the team to adapt their process after various limitations in the tool in a detrimental way, the breakdown of stories into various tasks during the planning risks ending up with developers losing track of the forest (value) for all the trees (tasks).

Thus, setting a sprint goal formulated in business terms and understandable by external stakeholders helps give the team a compass to remain focused on the user value. This also ties back to the idea of defining 'how to demo' in the user story. If the work doesn't achieve an output that is demo:able in some form, then odds are you have lost focus on creating actual value to stakeholders.

### Velocity
> What about a story that got almost completed during a sprint? Why don’t we get partial points for that in our actual velocity? Well, this is to stress the fact the Scrum (and in fact agile software development and lean manufacturing in general) is all about getting stuff completely, shippably, done! The value of stuff half-done is zero (may in fact be negative).

I found this part very interesting. I am not sure I agree about this point, as it can be seen as demotivating that works goes unrecognized in the burn-down chart for the sprint. The story estimation will either way need to be adjusted in the backlog since the actual remaining works has decreased.

Still, the point that unfinished stuff providing no value is true and considering the opportunity cost of not having worked on something else that might have been shipped to provide actual value, there is a clear logic in not recognizing work not completed. I expect this to be something I mull over for some time to come.

### Definition of "Done"
Classic source of frustration when there are different interpretations. Besides agreeing on a standard definition of what is to be considered done, in my experience this is best handled by defining unambiguous acceptance criteria that are objectively measurable. These also, of course, need to be within the scope of what the team has control over, if there are external dependencies, the team can not be blamed for not being able to complete the story.

If the team oftentimes do end up blocked from completing stories to an extent that is reasonably can be called done, then that suggests that there are organizational issues with how the team is setup.

**In addition to the acceptance criteria for something to be considered done, I'm getting more and more interested in the idea of success criteria. I.e., in addition to knowing whether a story was finished, there's an additional follow-up to see whether the story was a success or not.** This ties back to having a clear understanding of the customer needs, and being able to see the impact of work done. If completed user stories ends up not having much real world impact, then it was probably not the best investment of the teams time which suggests there might be time to do some self analysis - how come this work ended up being prioritized in the first place?

### Retrospectives
> One person (in this case, me) attends all sprint retrospectives and acts as the knowledge bridge. Quite informal.

Promising if it is a person all the teams trust!

> We’ve found that, in many cases, just identifying a problem clearly is enough for it to solve itself automatically next sprint.

In many cases this is true, and a great argument for why the retrospectives should be had even if they at time feel unproductive (no actionable outcome). Beware though if the same problem keeps reappearing, then it's clearly not enough to just identify it.
