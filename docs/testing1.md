  <a name=top><p>&nbsp;<hr>
  <p align=center>
  &nbsp;<a href="/README.md#top">home</a> &nbsp; | &nbsp;
  <a href="/docs/syllabus.md#top">syllabus</a> &nbsp; | &nbsp;
  <a href="https://docs.google.com/spreadsheets/d/1KuW-SH46KmFW0grEX2wT01jicUSew_5sr1QdGuSrweU/edit#gid=0">groups</a> &nbsp; | &nbsp;
  <a href="https://moodle-courses2223.wolfware.ncsu.edu/course/view.php?id=1771">moodle</a> &nbsp; | &nbsp;
  <a href="https://ncsu.hosted.panopto.com/Panopto/Pages/Sessions/List.aspx#folderID=%22389b8ebf-2f29-4c15-8231-aee9000e3f05%22">video</a> &nbsp; | &nbsp;
  <a href="/docs/review.md">review</a> &nbsp; | &nbsp;
  <a href="/LICENSE.md#top">&copy; 2022</a></p>
  <hr>
  <p align=center><a href="/README.md#top"><img  width=700 src="/etc/img/banner.png"></a></p>



# Testing 1


##  The Truth About Testing

- "Don’t worry if it doesn’t work right.  If everything did, you’d be out of a job."
  -  Mosher’s Law of Software Engineering
- "One (person)’s crappy software is another man’s full time job."
  -  Jessica Gaston

Testing bingo: do you know  these terms?


- Definitions
  - V-diagram, requirements (are a dirty word?),
  - unit test, systems test, integration test, acceptance test (alpha, beta),
    contractual and regulatory
  - state space
  - Goals: functional (e.g. Performance), non-functional (e.g. the "ilities... can you name three?)
- Testing is East: Test-driven development
  - is a useful process (for small teams)
  - gets very complex for large teams
  - is not a quality assurance activity
  - red, green, refactor
- Testing is hard
  - Infinitely good tests are infinitely expensive

Lateri (see [testing2](testing2.md):

- Types of testing
  - black box (aka functional), all-pairs, metamorphic testing, fuzzing (dumb, generational,
    mutation, coverage)
  - white box, formal testing
  - Coverage criteria: path, state, transition, function, statement, du, branch
- Test case prioritization
  - O'nite regression tests
    - Triage
- Software works (usually). Why? How can we exploit that?

## Quotes

- f u cn rd ths, u cn gt a gd jb n sftwr tstng.<br>
  - Anonymous
- "Program testing can be a very effective way to show the presence of bugs, but is hopelessly inadequate for showing their absence."<br>
  -  Edsger Dijkstra
- If debugging is the process of removing bugs, then programming must be the process of putting them in.<br>
  - Edsger Dijkstra
- Beware of bugs in the above code; I have only proved it correct, not tried it.<br>
  - Donald Knuth
- ... it is a fundamental principle of testing that you must know in advance the answer
   each test case is supposed to produce. If you don't, you are not testing; you are experimenting."<br>
  - Kernighan and Plauger
- Debugging is like a mystery novel where you are both the
  detective and the murderer.
  - Anon

## History

Testing had to be discovered:
- It was on one of my journeys between the EDSAC room and the
  punching equipment that ‘hesitating at the angles of stairs the
  realization came over me with full force that a good part of the
  remainder of my life was going to be spent in finding errors in
  my own programs.
  - Maurice Wilkes 1951

First bug

<img width=600 src="https://www.globalapptesting.com/hs-fs/hubfs/the-first-ever-bug---debugging.jpg?width=2160&name=the-first-ever-bug---debugging.jpg">

Testing is most of our effort:

<img width=600 src="https://github.com/txt/se20/blob/master/etc/img/vdiagram.png">

- V-diagram
  - "Without requirements or design, programming is the art of adding bugs to an empty text file."
    -- Louis Srygley
  - Brooks, [Mythical Man Month](https://web.eecs.umich.edu/~weimerw/2018-481/readings/mythical-man-month.pdf).
    Effort is
    - 1/3 th planning
    - 1/6 th coding
    - 1/4 th unit testing
    - 1/4 th systems testing


## Some Introductory Terms

- Unit tests: testing your code
- Systems test: testing how your code works with everyone else's (harder)
- Integration testing: verify the interfaces between components against a software design.
- Acceptance testing:
  - User acceptance testing
  - Contractual and regulatory acceptance testing
  - Alpha and beta testing
    - Alpha testing is simulated or actual operational testing by potential users/customer
    - Follows alpha testing: external testing with a larger audience
      - Released to a limited audience outside of the programming team
- State space: options inside a project
  - 300 boolean options = 2<sup>300</sup> states
    - Given numeric models, search space is infinite
  - Inside our software is more states than stars in the sky (10<sup>21</sup>)

## Testing for what?

- Documentation :
  - Incomplete, always
  - Even if we try to make it complete,complete for who
    - Stakeholders, competing goals
    - Toronto CS department. Information system
      - "good" if parents can track their children
      - "good" if students  can maintain their privacy
- For "maintainability?"
  - how to test that, except to watch the code for years to come?
- Performance:
  - Energy usage
  - Network request response time?
  - Minimize variance in query spike time

- For "usability"?
  - For other "ilities" (Maintainability, Customizanility,
    Scalability, Capacity, Availability, Reliability, Recoverability, Maintainability, Serviceability, Security, Regulatory, Manageability, Environmental, Data Integrity, Usability,
Interoperability

## Testing is Easy (not): Test-driven-Development

Have lots of unit tests!
Run them, a lot!
Get them all passing before checking back to main!
Do not make them into a  religion!

<img src="https://github.com/txt/se20/blob/master/etc/img/tddscreen.png">

Tests suites that run every time you save code

-  Build tests first
- Repeat:
  - Red = fund a broken test
  - Green= fix the test
  - Refactor= sometimes, clean things up
    - Refactoring means functionality _stays the same_ but the resulting _code is simpler_.

- Tips:
  - rerun "python3 mycode.py" or some pytest equalizing
  - keep the tests short (or else)

Test suites that you commit code.
  - `.travis.yml`
  - `.github/workflows/unittest.yml`
  - keep the tests short (perhaps, not so short)

Kent Beck, 2003:
- No studies have categorically demonstrated the difference between TDD and any of the many
  alternatives in quality, productivity, or fun.
  However, the anecdotal evidence is overwhelming, and the secondary effects are unmistakable

[David Hansson](https://www.youtube.com/watch?v=9LfmrkyP81M),  2013:
- Lots of developers that push TDD make you feel like your code is dirty if you are not using TDD.
- Driving your design from unit tests is not a good idea.
- The TDD notion of “tests must be fast” is shortsighted.
- The faith in TDD can lead to completely forgetting about system testing.
- The focus on the unit and the unit only does not help with producing a great system.
- 100% coverage is silly

Karac + Turhan (2018): TDD can't really be  defined or shown to be effective
- [What Do We (Really) Know about Test-Driven Development? ](https://www.researchgate.net/profile/Itir_Karac/publication/326239274_What_Do_We_Really_Know_about_Test-Driven_Development/links/5cee7550299bf1f881494cf6/What-Do-We-Really-Know-about-Test-Driven-Development.pdf)
   - Itir Karac and Burak Turhan

- TDD has too many cogs,
- Its effectiveness is highly influenced by the context (for example, the tasks at hand or skills of individuals),
- The cogs highly interact with each other
  - e.g. Insufficient TDD experience of knowledge
  - e.g.   Insufficient design
  - e.g. Insufficient developer testing kills,
  - e.g. Domain and tool specific limitations
  - e.g. Precedence of legacy code
  - e.g.  Insufficient adherence to TDD testing protocol,
    -  TDD isn’t a dichotomy in which you either religiously
        - write tests first every time
        - or always test after the fact.
        - TDD is a continuous spectrum between these extremes,
           - Developers tend to dynamically span this spectrum, adjusting the TDD process as needed
           -  Studies of 416 developers over more than 24,000 hours
               -  only 12 percent of the projects that claimed to use it, actually did
                  "write test first"
           - Studies of all Java projects in Github
             - applied heuristics for identifying TDD-like repositories
             - Only 0.8 % were TDD. And in that set, no evidence for
               - no evidence for higher commit velocity
               - no evidence for more issues reported or retired
  - Does TDD only perform better when compared to a coarse-grained
    rigid old-fashioned development waterfall process?
    - TDD’s superiority over a test-last approach were due to the fact that most of the
  experiments employed a coarse-grained test-last process closer to the waterfall
  approach as a control group

## Test is Hard

### What are you testing for?

- Testing to check that the promised behavior actually works?
  - But the documentation is incomplete, always
  - Even if we try to make it complete, complete for  who?
    - e.g. Stakeholders, competing goals
    - Toronto CS department. Information stem
      - "good" if parents can track their children
      - "good" if students  can maintain their privacy
    - How to write tests?
- Are any of the following mutually exclusive?
  - For "maintainability?"
    - how to test that, except to watch the code for years to come?
    - Research task: can we learn from prior maintainability?
  - Performance:
    - Energy usage
    - Network request response time?
    - Minimize variance in query   times
    - etc etc
  - For "usability"? Did you do that in HW3?
    - For other "ilities" (maintainability, customizability,
      scalability,
      capacity, availability, reliability, recoverability, maintainability,
      serviceability, security, regulatory, manageability, environmental,
      data integrity, interoperability fairness)

<img src="https://media.springernature.com/original/springer-static/image/chp%3A10.1007%2F978-3-319-18344-2_3/MediaObjects/335121_1_En_3_Fig5_HTML.gif">

### Testing is Hard: a little Maths

Consider test some web-based app
- Everything that happens to it depends on events, elsewhere on the web
- Those events happen at probability _p_
- So they don't happen at probability _(1-p)_
- So they don't happen after _n_ tests at probability _(1-p)<sup>n</sup>_
- So they do  happen after _n_ tests at probability
  _C(p,n) = 1- (1-p)<sup>n</sup>_
- That's a lot of tests

<img width=600 src="https://github.com/txt/se20/blob/master/etc/img/testmaths.png">

Problems:
- Infinite testing is infinitely expensive
  - rearranging
    _C(p,n) = 1- (1-p)<sup>n</sup>_
    we get
    _n = log(1-C) / log(1-p)_
  - For certainty (_C=1_) for low probability events (small _p=0_)  then _n_ explodes.
- Real world events hard to model with certainty
  - Events happen at probability _p_?
  - What _p_?

<img width=500 src="https://raw.githubusercontent.com/txt/ase16/master/img/notnorm8.png">

Also, what about rare events?

<img width=600 src="https://github.com/txt/se20/blob/master/etc/img/spike.png">

Can apply some non-simple stats to model arbitrary distributions as combinations of
(e.g.) Gaussian kernels (think wavlets or Fourier series, if you
know that stuff).

<img src="https://blogs.sas.com/content/iml/files/2016/07/kdecomponents1.png">

Or, for really weird functions, use non-parametric methods that divide the data into
chunks, then reasons separately about each chunk:

<img src="https://github.com/txt/se20/blob/master/etc/img/spiketree.png">

_______

To be continues (see [testing2](testing2.md)
