  <a name=top><p>&nbsp;
  <p align=center>
  &nbsp;<a href="/README.md#top">home</a> &nbsp; | &nbsp;
  <a href="/docs/syllabus.md#top">syllabus</a> &nbsp; | &nbsp;
  <a href="https://docs.google.com/spreadsheets/d/1sdIwdLxZ551NChuj5Pm9FCdRRhxVdVVIPgDpNg5ZFVY/edit#gid=0">groups</a> &nbsp; | &nbsp;
  <a href="https://moodle-courses2324.wolfware.ncsu.edu/course/view.php?id=4575">moodle</a> &nbsp; | &nbsp;
  <a href="https://ncsu.hosted.panopto.com/Panopto/Pages/Sessions/List.aspx?folderID=d992e131-df71-4368-940d-b064012a875c">video</a> &nbsp; | &nbsp;
  <a href="/docs/review.md">review</a> &nbsp; | &nbsp;
  <a href="/LICENSE.md#top">&copy; 2023</a><br>
  <a href="/README.md#top"><img   width=900 src="/docs/img/banner.png"></a></p><br clear=all>
  






## More Process Notes


Let us consider two extremes of software process: waterfall vs scrumm

![image](https://github.com/txt/se23/assets/29195/52c259a7-f480-422e-8f0a-b0acb33cfc8f)




Both are management tools for controlling software development.



## (aside: what is "Agile")

- Scrum is a type of agile
- Scrum is broken down into shorter sprints and smaller deliverables
-  In Agile, that is optional. In fact everything might be  delivered at the end of the project

<img src="https://sketchingscrummaster.files.wordpress.com/2020/06/agile-values-poaster-complete.png">

## Waterfall

- Making a good plan and sticking to it
-  Very efficient for well-defined projects



Large strategic control. Linear order of tasks:
- Requirements
- Analysis
- Design
- Code
- Test
-  Deploy


Experience gained from step i+1 only allowed to feed back to step i


Used for:

- For less complex projects with well defined requirements, processes and roles for team members.

- For large military or government contracts, often need to get approval for resources before moving ahead.  
  - In that context, the thing you are building is defined once at the start during a complex negotiation process
       known as the “requirements stage”
- For very long projects, software companies can’t afford to wait to the end to get paid. 
  - Waterfall offers landmarks along the way where non-programmers (read, accountants) can check off that some task is 
    completed (so they can pay for that stage).
- Hware/Sware co-design (see notes at end).

Less than useful when:


- Too much rigidity built into the project.
- Mid-project pivots require extensive re-engineering of the solution so far.
- When experience downstream in the process leads to massive changes to all ideas upstream (e.g. consider a single test shows that the whole system is too slow and needs massive redesign).
- Analysis paralysis: too much paper-driven activity, very little working code.


## Scrum

- Adapt, Improvise, Overcome
- High flexibility


- Smaller scale tactical meetings.
- A cycle that repeats in short cycles  (weekly or monthly)


Sprints:
1.    Review a backlog of “things to do”
2. select the things that deliver the most value at least cost.
3. Sprint to complete those tasks before the next review (next week, next month)
4. Go to step1


Daily meetings:
- Daily: run a meeting where everyone is standing up.  Ask everyone 3 questions:
- What have you accomplished since we last met?
- What do you plan to accomplish before the next meeting?
- What issues or problems are you currently facing?


Very useful when:

- When a project is based on incremental progress, complex deliverables or consists of multiple, not always sequential timelines.
- When dealing with small groups whose skills you trust, and no one is negotiating for specific dollar amounts before going ahead with the work.
- When running agile.
- When early feedback from running code can radically change your goals and designs.


Less than useful when:


- When small incremental change gets harder and harder since the overall architecture is now a mess.
- The project lost direction or is falling behind schedule.
- Constant iteration and re-alignment of the project is stretching budgets and timelines





## Notes from recent meetings with industry


AgileFall:
- we **say** we are agile but , actually, we **do** waterfall.


From an industry person: "have to get agile out of our copamany"
- for hardware / software co-design,  h/ware developers need a solid target for their work
- e.g. 4-6 month cycle
  a. Why,What,Who: motivations, users, user stories, high level decisions
  b. How : lower-level design
  c. Code : 
  d. Test : including h/ware integration
- Note: same people, cloud platform,s happy to see abcd cycles as short as 1 week.
