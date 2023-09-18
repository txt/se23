asda

## More Process Notes

Let us consider two extremes of software process: waterfall vs scrumm


Both are management tools for controlling software development.

## Waterfall

Large strategic control. Linear order of tasks:
- Requirements
- Analysis
- Design
- Code
- Test
-  Deploy

Experience gained from step i+1 only allowed to feed back to step i

Useful when:

- For large military or government contracts, often need to get approval for resources before moving ahead.  
  - In that context, the thing you are building is defined once at the start during a complex negotiation process
       known as the “requirements stage”
- For very long projects, software companies can’t afford to wait to the end to get paid. 
  0 Waterfall offers landmarks along the way where non-programmers (read, accountants) can check off that some task is 
  completed (so they can pay for that stage).

Less than useful when:

- When experience downstream in the process leads to massive changes to all ideas upstream (e.g. consider a single test shows that the whole system is too slow and needs massive redesign).
- Analysis paralysis: too much paper-driven activity, very little working code.


## Scrum

- Smaller scale tactical meetings.
- A cycle that repeats in short cycles  (weekly or monthly)

Sprints:
1.    Review a backlog of “things to do”
2. select the things that deliver the most value at least cost.
3. Sprint to complete those tasks before the next review (next week, next month)
4. Go to step1

Daily meetingsL
- Daily: run a meeting where everyone is standing up.  Ask everyone 3 questions:
- What have you accomplished since we last met?
- What do you plan to accomplish before the next meeting?
- What issues or problems are you currently facing?

Very useful when:

- When dealing with small groups whose skills you trust, and no one is negotiating for specific dollar amounts before going ahead with the work.
- When running agile.
- When early feedback from running code can radically change your goals and designs.

Less than useful when:

- When small incremental change gets harder and harder since the overall architecture is now a mess.


## Notes from recent meetings with industry

AgileFall:
- we **say** we are agile but , actually, we **do** waterfall.

From an industry person: "have to get agile out of our copamany"
- for hardware / software co-design,  h/ware developers need a solid target for their work
- e.g. 4-6 month cycle
  - Why,What,Who: motivations, users, user stories, high level decisions
  - How : lower-level design
  - Code : 
  - Test : including h/ware integration


