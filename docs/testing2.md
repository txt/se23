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
  






# Testing 2


## Types of Testing


###  Blackbox:
- Also known as _functional testing_
- Can't look inside the code
- e.g. Reflect on input space to find interesting regions
- e..g Look for clusters in the input or output space
  - e..g if age runs 0...120
    - try less-than-min, in-range, more-than-max
    - e.g. 1, 60, 150
  - e.g. all pairs testing
    - Let the inputs be a vector showing choices per input
      - Find inouts that never use the same pair of values, twice.
    - e.g. three binary inputs, one "days of week"
      and something with a range of 10 inputs
      - e.g. (happy:boolean rich:boolean healthy:boolean restDay:dayOfWeek exercise:1..10))
      - ranges:  (2 2 2 7 10)
      - so fi wever you use happy=true and restDay=sunday then you can never test that pair again
      - e.g. (t * * sunday *) can only appear once
    - when processed by an
      [_all-pairs_](ipo.lisp)
       generator
      `(ipo '(2 2 2 7 10))`  (see below)
    - BTW, all pairs is an amazing heuristic for exploring a large
      space
```lisp
((2 2 1 1 1) ; e.g. (true true true and first value of rest)
 (2 1 2 2 2) (1 2 2 3 3) (1 1 1 4 4)
 (2 2 2 7 5) (2 2 2 6 6) (2 2 2 5 7)
 (2 2 2 4 8) (1 1 2 1 9) (1 1 1 7 10)
 (1 1 1 6 5) (1 1 1 5 6) (2 1 1 3 3)
 (1 2 1 2 2) (2 2 1 7 9) (1 1 1 7 8)
 (1 1 1 7 7) (0 0 0 7 6)  ; note "0" means "don't care"
 (2 2 2 7 4) (0 0 0 7 3) (0 0 0 7 2)
 (1 1 2 7 1) (2 2 2 6 10) (0 0 0 6 9)
 (0 0 0 6 8) (0 0 0 6 7) (0 0 0 6 4)
 (0 0 0 6 3) (0 0 0 6 2) (0 0 0 6 1)
 (0 0 0 5 10) (0 0 0 5 9) (0 0 0 5 8)
 (0 0 0 5 5) (0 0 0 5 4) (0 0 0 5 3)
 (0 0 0 5 2) (0 0 0 5 1) (0 0 0 4 10)
 (0 0 0 4 9) (0 0 0 4 7) (0 0 0 4 6)
 (0 0 0 4 5) (0 0 0 4 3) (0 0 0 4 2)
 (0 0 0 4 1) (0 0 0 3 10) (0 0 0 3 9)
 (0 0 0 3 8) (0 0 0 3 7) (0 0 0 3 6)
 (0 0 0 3 5) (0 0 0 3 4) (0 0 0 3 2)
 (0 0 0 3 1) (0 0 0 2 10) (0 0 0 2 9)
 (0 0 0 2 8) (0 0 0 2 7) (0 0 0 2 6)
 (0 0 0 2 5) (0 0 0 2 4) (0 0 0 2 3)
 (0 0 0 2 1) (0 0 0 1 10) (0 0 0 1 8)
 (0 0 0 1 7) (0 0 0 1 6) (0 0 0 1 5)
 (0 0 0 1 4) (0 0 0 1 3) (0 0 0 1 2))
```


<img src="https://docs.microsoft.com/en-us/previous-versions/software-testing/images/cc150619.601ed013-938e-4e9e-bdb5-9b66bb49a5e0(en-us,msdn.10).gif">


## Blackbox (model-based)


- One trick in black box testing
  - Read the doc
  - Doodle a model showing expectations
  - Generate tests over that doodle


<img width=500 src="https://github.com/txt/se20/blob/master/etc/img/fsm1doc.png">


<img src="https://github.com/txt/se20/blob/master/etc/img/fsm1.png">


- Coverage criteria (for finite-state machines)
  - _Test coverage_: cover every path: no feasible due to infinite number of paths (cycles)
  - _State coverage_: every node coverage (minimal testing criterion)
  - _Transition coverage_: every edge covered
    - E.g. here are five tests covering every edge


<img src="https://github.com/txt/se20/blob/master/etc/img/fsm1edges.png">


- Is this still "just" functional testing.


### Blackbox Fuzzing


Dumb Fuzzing :


- Fuzz testing was originally developed by Barton Miller at the University of Wisconsin in 1989.
  - throw random cr\*p at a program till it crashed
  - brute force mutation
- History:
  - 1981: Duran and Ntafos investigated the effectiveness of testing a program with random inputs.
    - Previously: random testing had widely perceived to be worst means of testing
    - Their analysis: random proves are a cost-effective alternative to more systematic testing
  - 1983: Steve Capps developed "The Monkey", a tool that would generate random inputs for classic Mac OS applications, such as MacPaint.
     - The figurative "monkey" refers to the infinite monkey theorem which states that a monkey hitting keys at random on a typewriter keyboard for an infinite amount of time will eventually type out the entire works of Shakespeare. In the case of testing, the monkey would write the particular sequence of inputs that will trigger a crash.


  - 1988: Barton Miller: when he was logged to a modem during a storm, there was a lot of line noise generating junk characters and those characters caused programs to crash
     - New term: _fuzzing = automatically generate random files and command-line parameters
       for the utility.
     - The project was designed to test the reliability of Unix programs by executing a large number of random inputs in quick succession until they crashed.
  - Recently, numerous examples where fuzzing found bugs other approaches missed
- Simple fuzzing: advantages:
  - Very cheap to generate a test
  - Exploit CPUs to explore a broad range of options
  - Useful for dodging incorrect preconceptions of what the program should do
  - Good for detecting events that lead to  buffer overflow, DOS (denial of service),
    cross-site scripting and SQL injection
- Simple fuzzing: disadvantages:
  - It cannot provide a complete picture of the overall security, quality or effectiveness of a program
  - Spends much time generating impossible inputs or very unlikely events


Smarter fuzzing:


- Express input as a grammar
- Generate from tree
  - Generational fuzzing


```python
US_PHONE_GRAMMAR = {
     "<start>": ["<phone-number>"],
     "<phone-number>": ["(<area>)<exchange>-<line>"],
     "<area>": ["<lead-digit><digit><digit>"],
     "<exchange>": ["<lead-digit><digit><digit>"],
     "<line>": ["<digit><digit><digit><digit>"],
     "<lead-digit>": ["2", "3", "4", "5", "6", "7", "8", "9"],
     "<digit>": ["0", "1", "2", "3", "4", "5", "6", "7", "8", "9"]
}
```


- Example
```
[simple_grammar_fuzzer(US_PHONE_GRAMMAR) for i in range(5)]
['(692)449-5179',
 '(519)230-7422',
 '(613)761-0853',
 '(979)881-3858',
 '(810)914-5475']
```


Mutational fuzzing:


- Take a known valid input
- Mutate it


```python
def mutate(s):
    """Return s with a random mutation applied"""
    mutators = [
        delete_random_character,
        insert_random_character,
        flip_random_character
    ]
    mutator = random.choice(mutators)
    # print(mutator)
    return mutator(s)


for i in range(10):
    print(repr(mutate("A quick brown fox")))


'A qzuick brown fox'
' quick brown fox'
'A quick Brown fox'
'A qMuick brown fox'
'A qu_ick brown fox'
'A quick bXrown fox'
'A quick brown fx'
'A quick!brown fox'
'A! quick brown fox'
'A quick brownfox'
```


Coverage fuzzing


- Track parts of the grammar seen so far
- Fuzz to some new place.


Mining examples to weight crammers:


- Take a library of good examples
- Weight sub-trees on (e.g.) Probability
- Stochastic recursive descent:
  - Stochastically select sub-trees according to their weights
    - If weight = random then generational fuzzing
    - If select to prefer min weights, then coverage fuzzing
  - Recurs into sub tree.


Smarter smarter fuzzing = genetic programming


- We we dynamically adjust weights to prefer certain goals
  - then "testing" becomes AI
  - then "testing" becomes "mitigation" or "optimization"


### Metamorphic testing


How to test with an oracle for the specifics of the domain?


Metamorphic relations (MRs) are _necessary properties_ of the intended functionality of the software
- high-level statements that should be true across all inputs
- e.g. conjunctions do not lead to more output
   - RESULT1= "all males"
   - RESULT2="bald males"
   - RESULT2 should not be larger than RESULT1


- e.g. When testing a booking website, a web search for RESULT1= accommodation in Sydney, Australia, returns 1,671 results
    - RESULT2= Filter the price range or star rating and apply the search again;
    - RESULT2 should be a subset of RESULT1


A wonderful metamorphic testing result:  Z. Q. Zhou, T. H. Tse and M. Witheridge,
[Metamorphic Robustness Testing: Exposing Hidden Defects in Citation Statistics and Journal Impact Factors](https://www.cs.hku.hk/data/techreps/document/TR-2019-03.pdf) in IEEE Transactions on Software Engineering, doi: 10.1109/TSE.2019.2915065.


##  Whitebox::


White box: we can open up the code and look inside:


- Coverage criteria (for code)
  - Functions (all functions called once);
    - A very weak test
  - Statement coverage
    - Supported by many tools
  - du coverage:
    - find all paths between where a variable is _defined_ and _used_.
  - Branch coverage:
    - has every condition in the program be explored;
- Warning: you can succeed on all the above, and the code still crashes.


Symbolic execution:
- Find the abstract syntax tree of the code
  - e.g. python3's `ctree` package


```python
import ctree


def f(a):
    for x in range(10):
        a[x] += x


tree1 = ctree.get_ast(f)
ctree.ipython_show_ast(tree1)
```


<img src="https://ucb-sejits.github.io/ctree-docs/_images/ipython_example_tree_1.png">


Applications of symbolic execution:


- Walk the tree to collect the constraints to build the tests.
- Can lead to spectacular reductions to black box testing
- e.g. BigTest: White-Box Testing of Big Data Analytics [ESEC/FSE 2019]
  - Scripts processing gigabytes of  data sets
  - Is this a hard testing problem?
    - Q: Do the tests have to handle all the possible combinations in the data?
    - A: No: they only need to cover all the branches of the code


<img width=600 src="https://github.com/txt/se20/blob/master/etc/img/bigtest.png">


## Formal methods


Express english requirements as checkable logic, then use logic to reason about it


<img src="https://github.com/txt/se20/blob/master/etc/img/chat80.png">


Other examples:


- Product lines:


- [Truth-Functional Propositional Logic](https://www.cs.miami.edu/home/geoff/Courses/TPTPSYS/Practicum/EnglishToLogic.shtml)


- Temporal logic (add operators for until ("U") and always "[]" eventually "<>"
   - always &#8704;, there exists at least one &#8707;


<img src="https://github.com/txt/se20/blob/master/etc/img/scopes.png">


- e.g. elevator door stays open between X and Y


<img src="https://github.com/txt/se20/blob/master/etc/img/ltl.png">


(From [One-Click Formal Methods](http://www0.cs.ucl.ac.uk/staff/b.cook/oneclick.pdf):


- FORMAL METHODS: mathematically based approaches for specifying, building,
  and reasoning about software.
- Despite 50 years of research and development, formal methods have had
  only limited impact in industry.
- Some in such domains as microprocessor design and aerospace.


Why not widely used?


- _The modeling cost_:
  Analysts must create a systems model (what is the system)
  and a properties model (what is meant to do). Properties model
  usually much smaller than systems model.
- _The execution cost_: Rigorous analysis of formal properties needs a  full search of  systems model.
- _The personnel cost:_ Analysts skilled in formal methods must be recruited or trained.
  Such analysts are generally hard to find and retain.
- _The development brake:_ The above costs can be so high that the requirements must be
   frozen for some time while we perform the formal analysis.
   Hence, one of the costs of formal analysis is that it can slow the process of requirements evolution.


Recent experience at Amazon:


- More and more, web-based systems are configured in sufficient detail
  - Such that processes can be bounced around from node to node on the cloud (to make best use of spare resources)
  - Application program interfaces (APIs) of cloud services are computer-readable contracts that establish and govern how the system behaves.
    - Most importantly, since those models are utilized by a large user community,
      - now economically feasible to build the tools needed to verify them
  - Which means that we have enough information to auto-configure our formal methods
    - and the size of the potential user community and the business value now justifies the cost of formal methods.


<img width=600 src="https://github.com/txt/se20/blob/master/etc/img/3tiered.png">


## "Testing" and Product Lines and Formal Methods


A feature model is a "product line"; i.e. a description of a space
of products.


Question: what are the _different_ products we can pull from the following?


<img src="https://github.com/txt/se23/blob/main/docs/img/fm001.png">


Now that was a small feature model. Suppose we are talking about something
really big like a formal model of the LINUX kernel with 4000 variables
and 300,000 contrast. Q: How to reason over that space? A: use a theorem prover.
e.g. _Pycosat_.


The following example comes from the excellent documentation
at the
[Python Picostat Github page](https://github.com/ContinuumIO/pycosat/blob/master/README.rst)


Let us consider the following clauses, represented using
the DIMACS `cnf <http://en.wikipedia.org/wiki/Conjunctive_normal_form>`_
format::


        p cnf 5 3
        1 -5 4 0
        -1 5 3 4 0
        -3 -4 0


Here, we have 5 variables and 3 clauses, the first clause being


_x1  or not x5 or x4_


Note that the variable x2` is not used in any of the clauses,
which means that for each solution with x2 = True, we must
also have a solution with x2 = False.  In Python, each clause is
most conveniently represented as a list of integers.  Naturally, it makes
sense to represent each solution also as a list of integers, where the sign
corresponds to the Boolean value (+ for True and - for False) and the
absolute value corresponds to i-th variable::


        >>> import pycosat
        >>> cnf = [[1, -5, 4], [-1, 5, 3, 4], [-3, -4]]
        >>> pycosat.solve(cnf)
        [1, -2, -3, -4, 5]


This solution translates to: x1=x5=True,
x2=x3=x4=False


To find all solutions, use `itersolve`::


        >>> for sol in pycosat.itersolve(cnf):
        ...     print sol
        ...
        [1, -2, -3, -4, 5]
        [1, -2, -3, 4, -5]
        [1, -2, -3, 4, 5]
        ...
        >>> len(list(pycosat.itersolve(cnf)))
        18


In this example, there are a total of 18 possible solutions, which had to
be an even number because x2 was left unspecified in the clauses.


The fact that `itersolve` returns an iterator, makes it very elegant
and efficient for many types of operations.  For example, using
the `itertools` module from the standard library, here is how one
would construct a list of (up to) 3 solutions::


        >>> import itertools
        >>> list(itertools.islice(pycosat.itersolve(cnf), 3))
        [[1, -2, -3, -4, 5],
         [1, -2, -3, 4, -5],
         [1, -2, -3, 4, 5]]


### Example


Feature Models and Product Lines: [Software installation as a formal methods problem](http://cseweb.ucsd.edu/~lerner/papers/opium.pdf)


Lets represent software dependencies in a logical framework:


<img src="https://github.com/txt/se20/blob/master/etc/img/opium.png">


If we run Picosat over these formulae then:


- Any solution that satisfies all the constraints...
- Is a different way to create a valid install of the program.


Variants:


- min install:
   - add a cost to the install effort of each part
   - score everything coming out of `itersolve` (sum that cost)
   - pick the easiest thing to install
- optimizing:
   - generate one solution, ask some human what they think
   - if they don't like, negate it add it to the theorems
   - so future solutions will _not_ contain the thing you don;t like


**Important note:** in practice, except for trivally small
problems, no one writes DIMACS manually.


- Instead, we write code to generate DIMACS via some code.
- For example:
  [running code](https://github.com/ContinuumIO/pycosat/blob/master/examples/opium.py).


## Scale-up Issues


### Scaling up SAT Solvers


In summary, in theory, it is can be useful to reformulate SE tasks as a SAT task. As Micheal Lowry said at a panel at ASE’15:


- It used to be that reduction to SAT proved a prob- lem’s intractability. But with the new SAT solvers,
  that reduction now demonstrates practicality."


However, in practice, general SAT solvers, such as the Z3, MathSAT [29], vZ  et al.,
are challenged by the complex- ity of real-world software models. For example, the largest benchmark
for SAT Competition 2017 [31] had 58,000 variables– which is far smaller than (e.g.) the 300,000
variable problems seen in the recent SE testing literature [4].


So SAT solvers are great but as software gets really really big, they need help.


- [Scalable product line configuration: A straw to break the camel's back](https://www.semanticscholar.org/paper/Scalable-product-line-configuration%3A-A-straw-to-the-Sayyad-Ingram/3384176ef4196797603ae2ca68ff353bb4233668)
  Abdel Salam Sayyad, Joseph Ingram, H. Ammar, Tim Menzies
  2013 28th IEEE/ACM International Conference on Automated Software Engineering (ASE)
- [Building Very Small Test Suites (with Snap)](https://arxiv.org/pdf/1905.05358.pdf),
  Jianfeng Chen, Xipeng Shen, Tim Menzies, 2020


### Scaling up TDD


##### Continuous integration at Google


- Continuous change to the code base
- Continuous testing
- January to October 2013
  - Google ran 3 billion unit tests
  - Global network of machines
  - Problems
      - Running out of cpu
      - less that 0.5% of those tests ever failed
      - Long lags from submission to “passed
- Test case prioritization
  - Select test if (a)new, or (b)recently failed or (c) not recently executed
  - Found more tests that failed, much earlier
  - Greatly reduced time for programmers to get feedback


<img src="https://github.com/txt/se20/blob/master/etc/img/googletdd.png">


- Very many prioritization schemes
  - Different according to what information they need
  - [How Different is Test Case Prioritization for Open and Closed Source Projects?](https://arxiv.org/pdf/2008.00612.pdf),
    Xiao Ling, Rishabh Agrawal, and Tim Menzies.


##### Continuous  integration at Lexis Nexis


<img src="https://github.com/txt/se20/blob/master/etc/img/lnseip.png">


Large overnight run of all tests.
- when something crashes, there is no link of crash back to line numbers. Pause. What?
- Turns out, there is no information in that.
  - When something crashed, it coes to an off shore team of experts to decide which teams (back in the USA) need to fix
    the bug).


General lesson:
- Need to test  less


- [TERMINATOR: Better Automated UI Test Case Prioritization](https://arxiv.org/pdf/1905.07019.pdf),
  Zhe Yu, Fahmid Fahid, Tim Menzies, Gregg Rothermel, Kyle Patrick, Snehit Cherian,
  (ESEC/FSE ’19, SEIP), August 26–30, 2019, Tallinn, Estonia.


<img src="https://github.com/txt/se20/blob/master/etc/img/howprior.png">


<img src="https://github.com/txt/se20/blob/master/etc/img/zhe.png">


## The Big Question


Q: Why does testing work?
  - A: Software runs in a small part of the total space


Marek Druzdzel, diagnosis
- application for monitoring patients in intensive care.
- software had 525,312 possible internal states
- the application reached few of them at run time:
   - one of the states occurred 52 percent of the time,
   - 49 states appeared 91 percent of the time.


<img src="https://github.com/txt/se20/blob/master/etc/img/druzdel.png">


NASA software data: Most faults lie in a small proportion of the files.


- T. Menzies, J. Greenwald and A. Frank, "Data Mining Static Code
Attributes to Learn Defect Predictors," in IEEE Transactions on
Software Engineering, vol. 33, no. 1, pp. 2-13, Jan. 2007, doi:
10.1109/TSE.2007.256941.


AT&T software data: about 80% of the defects come from 20% of the files


- Ostrand et al., “Where the Bugs Are,” Proc. ACM Int’l Symp. Software Testing and Analysis, 2004.


Ditto for the GNU "C" compiler, GCC


- Hamill, Goseva-Popstojanova, Common Trends in Software Fault and Failure Data IEEE TSE, 35(4) 2009


<img src="https://github.com/txt/se20/blob/master/etc/img/gcc.png">


Jospeh Horgan and Aditya Mathur reported in “Software Testing and
Reliability” that testing often exhibits a “saturation effect”;
i.e. most program paths get exercised early with little further
coverage improvement as testing continues.


- see The Handbook of Software Reliability Engineering, 1996).


As to mutation testing, Christopher Michael found that in 80 to 90\%
of cases, there were no changes in the behavior of a range of
programs despite numerous perturbations on data values using a
program mutator


- C.C. Michael, ‘On the uniformity of error propagation in software’, Proceedings of the 12th Annual Confererence on Computer Assurance (COMPASS ’97) Gaithersburg, MD, 1997.


So do not poke everything, everywhere
- Rather, poke around, some
- Where anything starts to fail,
- Move in for a closer look


Don't believe me? Well...


- Fuzzing... works
- Metamorphic testing... works


But what about safety critical applications?


- Demand vastly simpler code
- Tested using vastly longer testing cycles
- Test generated via a very thorough requirements process.


For more see:
- The Strangest Thing About Software. Available from:
https://www.researchgate.net/publication/2961707_The_Strangest_Thing_About_Software


