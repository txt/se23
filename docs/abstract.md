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
  






<img src="https://raw.githubusercontent.com/txt/se20/master/etc/img/abstract.png">


Historically, abstraction has enabled:


- millions of useful tools, class libraries
- billions of  dollars in the  acquisition of novel tech companies (see below)
- the teaching of software engineering (since it lets us teach  many concrete ideas with a smaller number of abstractions);
- testing
  - abstracting lots of functionality into 
    - a small number of tests 
    - that cover much of the functionality
- hardware-independent  programming language and operating systems
  - so very large communities of programmers to co-ordinate with each other 
- cloud computing
- And, well, everything
  - Is abstraction the core of everything we do?
  - Is the whole history of computer science is the search for
    usefuls, implementable,  abstractions?


## What is abstraction?


Formal definition 
- abstraction = freedom from representational qualities 
- i.e. a step above the details to... something else


Between the programmer and the lower-level details (e.g. the hardware, the lower-level language constructs) there is a  layers of abstraction
- Programmers talk to the abstraction
- Automated tools map the  abstraction to something lower down


Concrete example of abstraction:


1. Concrete: Countries have states. States have cities. Cities have suburbs. Suburbs have streets. Streets have houses.
2. Abstract: Things, at level `i` have sub-things at level `i+1`.
   - Note that number 2, would need some tools for instance creation
   - Maybe something as simple as a yaml config file to make your country


If you are only building one application, then clearly number1
- And if you racing to get "it" out the door then there is clearly a case for using the first, most obvious design.


But
- If you are testing "it" then
  - abstractions reduce the number of tests. 
  - eg. in the above, one test, not four
    - Abstract: 
      - if we delete things, do we also delete sub-things versus
    - Concrete:
      - if we delete suburbs,  do we also delete streets?
      - if we delete cities,  do we also delete suburbs?
      - if we delete states,  do we also delete cities?
      - if we delete countries,  do we also delete states?
 - If after doing "it",
   - And if you want to support very large communities not just doing "it0" but also "it1, it2..."
   - And you want to build something unique that might be the basis for an entirely new industry 
     - Supporting billions of dollars in IT acquisitions
   - Then you need abstraction.


## Kinds of abstractions


Abstraction  has been applied, successfully, dozens of times in the history of computing
- All these following use the same idea... abstraction


The following list is sorted
  by their memory footprint, largest to smallest:


1. Operating systems
2. Virtual machines
3. Containers
4. Serverless systems
5. Erlang's trick
6. Unix Pipes
7. OO class hierarchies
8. Macros
9. Iterators and error handlers
   - These last two is not the same as the rest
     - Iterators and error handlers are abstraction tricks for programmers are smaller than
     - Implemented and popularized by Barbara Liskov
   - The  rest allow you jump computation around one of more CPUs


Also, for other notes on abstraction that lead to different
 programming languages (LISP, Smalltalk, Java, Javascript, CoffeeScript)
- see next lecture


## Why abstraction?


- Aesthetics:  
  - Truth is beauty and beauty is truth and darn I love me a good abstraction
  - Is the whole history of science trying to prove "x" (where "x" is an abstraction standing in for multiple concrete things)?
- Innovation: abstraction + tool support 
  - Roll your own tech company
- Simplicity: 
  - If you underlying data structures are complex, 
    - you want some way to talk to them without having to know everything about them
  - Combine N concrete things into one abstract thing 
    - e.g. see above, testing
    - e.g. [mustache macros](https://mustache.github.io/)
    - e.g. [docopt](https://github.com/docopt)
- Portability: If you want to run your code on a range of different hardware
  -  you want to write code in  hardware independent manner
     - so code can run all over the place
  - Add an abstraction layer between
    - operating systems below and
    - the application above
    - Once you get "it" going for one OS on one machine
      - It runs wherever that OS runs
    - e g. 
     - UNIX (see below)
     - Some abstractions make things so easy, can port then to many langauges
       - mustache
       - docopt
- Scheduling: If computing environments are dynamic, we want to bounce our
computation around the hardware to take full advantage of unused
resources.
   - And when we bounce a "program", we want to bounce with it:
       - all the current
     variable settings, 
       - contents of RAM, 
       - activation records of current
     functions, 
       - return addresses for when those functions return, 
       - network
     connections, 
       - hooks to GUIs and databases, etc etc. 
   - Think of the _layers_ pattern, on steroids
       - Where you grab whole layers and move them to another piece hardware
   - Under the hood, again, this is abstraction.


## How to abstract
Warning:
- Good abstractions needs experience
  - To see across multiple applications
- Good abstractions need test cases
  - To test out the practicality, utility of things like number2
- Suggestion: rule of three
  - First time, just do concretely
  - Second time, be concrete again, but make a little note
  - Third time: "not you again? time to abstract!"


BTW, best abstractions needs really, really smart people


- Barbara Liskov won at $250K prize for her work on  abstraction in programming languages.
  - [Her award lecture](https://amturing.acm.org/vp/liskov_1108679.cfm)
    is amazing
    - at minute  1:09:00 to 1:11:00 the whole world disappears and her and Guy Steele (\*)debate
      iterator design and the rest of us can just listen


<em>(\*) You don't know who Guy Steele is? Shame on you! [Read it](https://apps.dtic.mil/dtic/tr/fulltext/u2/a030751.pdf) and weep.</em>


 
## Error handling


Throw a ball into a stadium, wait for what returns while holding a catchers mitt.
Only catch things you know how to handle


```python
def atom(token: str) -> Atom:
    "Numbers become numbers; every other token is a symbol."
    try: return int(token)
    except ValueError:
        try: return float(token)
        except ValueError:
            return Symbol(token)
```


## Iterators


When you code recursive data structures, give programmers
so way to way around that code.


e.g. What does this return?


```python
def items(x):
  if isinstance(x,(str,list,tuple)):
    for y in x:
      for z in items(y):
        yield z
  else:
    yield x


for x in items([10,[[11,12,13],15], 20,30,[40,50,"tim"]]):
   print(x)
```
Another example (in awk). This example shows that _iterators_ can be implemented in any language,
it you think the right way.


```awk
# application code


while(csv(lst,file))
  doSOmething(lst)
```


Handles numerous details for reading CSV files. For example, the following 
CSV file has blank lines (to be skipped),  white space and comments (that need deleting), 
strings containing numbers that need to be coerced into real numbers,
and record that that split on "," (which need to be combined with the next line).


```
name,   # who
age,    # in year`s
shoesize # posint
#########################


# family1
tim, # what
21,  # a 
10   # nice guy
jane  ,  6,  2


# family2
tim, 21, 10 
jane,6,2
```
The `csv` iterator reader is below. This iterator calls a sub-iterator `getline` that returns 0 on end of line:


```awk
# iterator code


function csv(a,file,                        # passed arguments     
             i,j,b4, ok,line,x,y) {         # locals
  file  = file ? file : "-"                 # [1] ... read from standard input or file       
  ok = getline < file
  if (ok <0) {                              # [2] ... complain if missing file
     print "missing "file > "/dev/stderr"; 
     exit 1 }
  if (ok==0) { close(file);return 0 }       # [3] ... signal that there is no data                                 
  line = b4 $0                         
  gsub(/([ \t]*|#.*$)/, "", line)           # [4] ... kill white space and comments      
  if (!line)       return csv(a,file, line) # [5] ... skip blanks lines
  if (line ~ /,$/) return csv(a,file, line) # [6] ... contact incomplete rows with next
  split(line, a, ",")                       # [7] ... split line into cells on comma
  for(i in a) {
    x=a[i]
    y=a[i]+0
    a[i] = x==y ? y : x                     # [8] ... coerce number strings, if any
  }
  return 1                                  # [9] ... signal that there is more to come
}
```


The point being made here is that "abstraction" is a tool you can use, in any language
- You just need to think a little more... abstractly
- Thing "producer" and "consumer" when the consumer does not want to, or need to, understand all the details
  - Which is very useful if I start changing low-level representations
    - e.g. I'm talking to a zip file and not a raw file
    - Then `csv` can change internally while the application code remains the same.


By the way, if we are talking abstractions about consumers and producers then that takes us naturally to pipes (see below)


## Pipes


Doug McIlroy, Bell Labs’ “Computing Techniques
Research Department” 1986
-   “We should have some ways of coupling programs like garden hose.” 
- "Let programmers screw in another segment when it becomes necessary
to massage data in another way.”
- “Expect the output of
 every program to become the input to another, as yet unknown,
 program. Don’t clutter output with extraneous information.”


Pipes changed the whole idea of UNIX:


- Implemented in 1973 when ("in one feverish night",
wrote McIlroy) by  Ken Thompson.
- “It was clear to everyone, practically minutes after the system
came up with pipes working, that it was a wonderful thing. Nobody
would ever go back and give that up if they could.”
- The next
day", McIlroy writes, "saw an unforgettable orgy of one-liners
as everybody joined in the excitement of plumbing." 


Pipes changed how we think about software


- Not applications
- But tools.
  - Compose the things together, if you
had made them so that they actually worked together. 
  - People went back and consciously put into programs the idea that they read from a list of files 
  -  And  if there were no files they read from the standard input so that they could be used in pipelines.


You've probably all used pipes already. Here we download an install shell script  then pipe it to the `sh` command
(so it runs)


```
curl -s http://example.com/install.sh | sh
```


(By the way, that is a security risk. [Use with care!](https://blog.dijit.sh//don-t-pipe-curl-to-bash))


Examples
- `nroff` is a text formatter (old version of latex)
- `lp` is the line printer
- `col` handles escape sequences that sets up text in 2 columns
- `tbl` is an nroff pre-processor that expresses tables in terms of lower-level nroff commands
- `eqn` is an nroff pre-processor that expresses equations in terms of lower-level nroff commands


```bash
nroff files | col | lp


tbl file-1 file-2 . . . | eqn | nroff -ms
````


Think of pipes as `produce`, `translate`, `filter`, `consume`:


```bash
find /usr/bin/ |                #produce 
sed 's:.*/::'  |                #translate: strip directory part
grep -i '^z'   |                #filter   : select items starting with z
xargs -d '\n' aFinalConsumer    #consume 
```


Note that in the above, the `filters` inside the `pipes` could be written in any language at all, by different teams.


Also, operating systems _love_ pipes since they can run each part of the process as a separate process,
maybe even on different machines (\*)


(\*) That said, there is the data bus / network cost of streaming data between parts of the pipe. 


Problems with pipes:


- Assumes a one-way flow, here to there
  - Not ideal for GUI envrionments where users want to call functions in any order
  - Which makes pipes are more an "under the hood" idea
- Also, I've had problems with pipes and concurrency: sending data off on long retrevial arcs (e.g. from another part of the network)
  - But that's just me


## OO Class Hierachies


Smalltalk class hierarchy (somewhere in the 1980s)
- Count the "abstract classes" (mostly, the non-leaf classes)
  - i.e. classes that will never be instantiated
  - but exist to defined shared properties of the subclasses.
  - my counts is 40% "abstract"; i.e. nearly half.
    - That's a lot of abstraction!


<img align=right src="https://i.pinimg.com/originals/e2/c1/4a/e2c14a7f83ea042e9dc8e0031e5e1a72.jpg">


```
Object
|    Behavior
|    |    ClassDescription
|    |    |    Class
|    |    |    Metaclass
|    BlockClosure
|    Boolean
|    |    False
|    |    True
|    Browser
|    Collection
|    |    Bag
|    |    MappedCollection
|    |    SequenceableCollection
|    |    |    ArrayedCollection
|    |    |    |    Array
|    |    |    |    ByteArray
|    |    |    |    WordArray
|    |    |    |    LargeArrayedCollection
|    |    |    |    |    LargeArray
|    |    |    |    |    LargeByteArray
|    |    |    |    |    LargeWordArray
|    |    |    |    CompiledCode
|    |    |    |    |    CompiledMethod
|    |    |    |    |    CompiledBlock
|    |    |    |    Interval
|    |    |    |    CharacterArray
|    |    |    |    |    String
|    |    |    |    |    |    Symbol
|    |    |    LinkedList
|    |    |    |    Semaphore
|    |    |    OrderedCollection
|    |    |    |    RunArray
|    |    |    |    SortedCollection
|    |    HashedCollection
|    |    |    Dictionary
|    |    |    |    IdentityDictionary
|    |    |    |    |    MethodDictionary
|    |    |    |    RootNamespace
|    |    |    |    |    Namespace
|    |    |    |    |    SystemDictionary
|    |    |    Set
|    |    |    |    IdentitySet
|    ContextPart
|    |    BlockContext
|    |    MethodContext
|    File
|    |    Directory
|    FileSegment
|    Link
|    |    Process
|    |    SymLink
|    Magnitude
|    |    Association
|    |    Character
|    |    Date
|    |    LargeArraySubpart
|    |    Number
|    |    |    Float
|    |    |    Fraction
|    |    |    Integer
|    |    |    |    LargeInteger
|    |    |    |    |    LargeNegativeInteger
|    |    |    |    |    LargePositiveInteger
|    |    |    |    |    |    LargeZeroInteger
|    |    |    |    SmallInteger
|    |    Time
|    Memory
|    Message
|    |    DirectedMessage
|    MethodInfo
|    Point
|    ProcessorScheduler
|    Rectangle
|    Signal
|    |    Exception
|    |    |    Error
|    |    |    |    Halt
|    |    |    |    |    ArithmeticError
|    |    |    |    |    |    ZeroDivide
|    |    |    |    |    MessageNotUnderstood
|    |    |    |    UserBreak
|    |    |    Notification
|    |    |    |    Warning
|    Stream
|    |    ObjectDumper
|    |    PositionableStream
|    |    |    ReadStream
|    |    |    WriteStream
|    |    |    |    ReadWriteStream
|    |    |    |    |    ByteStream
|    |    |    |    |    |    FileStream
|    |    Random
|    |    TextCollector
|    |    TokenStream
|    UndefinedObject
|    ValueAdaptor
|    |    NullValueHolder
|    |    PluggableAdaptor
|    |    |    DelayedAdaptor
|    |    ValueHolder
```


- More on "Streams"
  - Streams are objects that support sequential access to collections and files of sequential data. Streams can be open on sequenceable collections of any kind of object, on a source of random numbers, or on files.
  - There are two separate sets of stream classes, one for streams on collections, and one for streams on files.
  - More on "Random" as a stream:
    - [FileStream atEnd](https://github.com/bonzini/smalltalk/blob/master/kernel/FileStream.st#L528-L533)
      -  produces a finite stream of characters, terminating at end of file
    - [Random atEnd](https://github.com/bonzini/smalltalk/blob/master/kernel/Random.st#L110-L115)
      -  produces an infinite stream of machine-generated pseudo-random floating-point numbers of good quality in the range 0.0 through, but not including, 1.


[On the criteria to be used in decomposing systems into modules](https://blog.acolyer.org/2016/09/05/on-the-criteria-to-be-used-in-decomposing-systems-into-modules/).
David Parnas, 1971
- Death to flowcharts! (and, by implication, pipes)


## Macros


The LISP `dolist` macro lets you do things to `one` item ata  time from a `lst` (list).


e.g.
```lisp
(dolist (one lst) 
   (print one))
```


What does this high level abstraction hide under-the-hood?


Lets find out:


```lisp
[3]> (macroexpand-1 '(dolist (one lst) (print one)))


(DO* ((#:LIST-2990 LST (CDR #:LIST-2990))
      (ONE NIL))
     ((ENDP #:LIST-2990) NIL)
     (DECLARE (LIST #:LIST-2990))
     (SETQ ONE (CAR #:LIST-2990))
     (PRINT ONE)
)


[3]> (macroexpand-1 (macroexpand-1 '(dolist (one lst) (print one))))


(BLOCK NIL
       (LET* ((#:LIST-2991 LST)
              (ONE NIL))
             (DECLARE (LIST #:LIST-2991))
             (TAGBODY #:LOOP-2992
                      (IF (ENDP #:LIST-2991)
                          (GO #:END-2993))
                      (SETQ ONE (CAR #:LIST-2991))
                      (PRINT ONE)
                      (SETQ #:LIST-2991
                            (CDR #:LIST-2991))
                      (GO #:LOOP-2992)
                      #:END-2993
                      (RETURN-FROM NIL
                                   (PROGN NIL))))) ;
```


Note that `defmacro` is a LISP built in that lets you write your own macros. Note that a Python variant
of this become so acrimonious that  [Python's founder resigned from the community](https://lwn.net/Articles/759654/). LISP programmers would just shrug and say "whatever, use it, don't use it, up to you".


```lisp
(defmacro aif (test-form then-form &optional else-form)
   `(let ((it ,test-form))
          (if it ,then-form ,else-form)))


 (aif (+ 2 7)
   (format nil "~A does not equal NIL." it)
   (format nil "~A does equal NIL." it))
 ;; ⇒ "9 does not equal NIL."
```


LISP is not so popular these days. For cool languages that support macros:


- use LISP (hey, still lots of support and development)
- but look at JULIA also (a hot new language)!


## Queuing Theory 


Before going on... this is going to seem a digression, but just stay with me here


The point of this little digression is that it is useful to jump around things
between service providers. 
- And the smaller the thing, the faster we can jump it
- And the more little gaps we can jump them into


N tellers/ checkout people. How many lines? One? N?


<img src="https://operationsroom.files.wordpress.com/2016/10/na-cl845_number_16u_20161006202714.jpg" width=700>


Answer: see [7 insights into Queue Theory](http://www.treewhimsy.com/TECPB/Articles/SevenInsights.pdf)


[According to the RIOT paper](https://arxiv.org/pdf/1708.08127.pdf)
Computers
execute in highly dynamic environment.


- For example, Schad et al. [11] found that the
runtime of a widely used benchmarks suite can vary by up
to 33% even when run on supposedly identical instances
within the same cloud environment. 
- Not only CPU, but
also bandwidth can be highly variable within the cloud.
  - Schad et al. report that network bandwidth between the
same type of EC2 instances can vary from 410KB/s to
890KB/s. 
- Hence, even after a workflow is planned and
deployed, it is important to monitor instances and repeat
the scheduling process during deployment when necessary.
- If repeated rescheduling are too slow, then there is much waste of computer rescues.


## Erlang's Trick


Some languages are designed for concurrency. To do so, they use new abstractions.


Consider the following block-structured programs (where variables in a sub-block can access variables in parent blocks):


```python
def aa(x):
    def bb(y): return aa(y-1)
    return x if x < 1 else bb(x)
```


Here, we can't run ``bb`` by itself without dragging along everything we know about ``aa`. 


So instead, what if all functions are in the global space and all variables can only access the local space of each function?


Here's a small database language that can derive child info from a database on `father`s and `mother`s.
`X` and `Y` are variabes scoped to within a `clause` (and clauses end with a _fulll stop_).


```prolog
child(X,Y) :- mother(X,Y).  # clause1
child(X,Y) :- father(X,Y).  # clause2


descendant(X,Y) :- child(X,Y).                    # clause3
descendant(X,Y) :- child(X,Z), descendant(Z,Y).   # clause4


father(tim,don).            # clause
father(janet,don).          # clause6


mother(tim,jane).           # clause7
mother(janet,don).          # clause8
```


Note now that the clauses can all be run seperately on different CPUs since everything we need to know about (eg) `descendant`
is available locally when we call that function.


Now Erlang's _unit of swap_ is really, really small. From
[Erlang](https://www.infoq.com/presentations/erlang-software-for-a-concurrent-world/) 
- Erlang is a concurrent language. 
- By that I mean that threads are part of the programming language, they do not belong to the operating system. 
- That's really what's wrong with programming languages like Java and C++. 
  - It's threads aren't in the programming language, threads are something in the operating system s
    – and they inherit all the problems that they have in the operating system. 
- One of those problems is granularity of the memory management system. 
  - The memory management in the operating system protects whole pages of memory, 
     so the smallest size that a thread can be is the smallest size of a page. 
  - That's actually too big.
  - If you add more memory to your machine – you have the same number of bits that protects the memory 
    so the granularity of the page tables goes up – you end up using say 64kB for a process you know running in a few hundred bytes.


Sounds like a crazy idea, right? Well, its actually a crazy 19 billion dollar idea.


- 2015 WhatsApp aqcuired by Facebook
- 50 engineers running software for a billion users
- Erlang particularly suited to juggling communications from a huge number of users, and it lets engineers deploy new code on the fly
- E.g. [watch at home (NSFW)](https://www.youtube.com/watch?v=rRbY3TMUcgQ). 
  - See their intro-demo: a chat bot with 300,000 users sending near instant updates to each other.


And its not just one company:


-  Cisco ships 2 million devices per year running Erlang (comments at the Code BEAM Stockholm conference in 2018).
  -  This translates to 90% of all internet traffic going through routers and switches controlled by Erlang. 
-  Ericsson has Erlang at the core of its GPRS, 3G, 4G and 5G infrastructure. 
   - With a market share of 40%, there’s a high probability a program written in Erlang assigned the IP address your smartphone is using today 
     (amongst other things).
   - Since being released as open source, Erlang has been spreading beyond Telecoms, establishing itself in other verticals such as 
       FinTech, Gaming, Healthcare, Automotive, IoT and Blockchain. 
- For more see [here](https://www.erlang-solutions.com/blog/which-companies-are-using-erlang-and-why-mytopdogstatus.html)
  - e.g. English National Health Service (NHS). 
  -  The NHS obviously requires high availability and handles over 65 million record requests every day through its 
     Spine, a centralised point allowing the exchange of information across national and local systems. 
     Using Riak (written in Erlang), the NHS has managed 99.999% availability for over five years.
  
See also Elixr (Erlang + prettier syntax, not sure it has the same systems advantage as Erlang).


## Serverless


Servless is an abstraction that is smaller than containers


[demo](https://swizec.com/412eabb35fe281cb452e125f38b49f56/Vercel-cloud-function-demo884651.gif)


- Serverless
  - e.g. AWS Lambda (btw, why is it called "lambda"? See below).
  - Why even have an operating system, just start with your current application and only ship the little bits
    needed for the application
  - Good news:
    - Cheaper
    - Smaller memory (so more scalable)
    - Productivity: less to configure, less messing with threading.
      Just explore  the unit of code to the outside world are simple event driven functions.
  - Bad news:
    - Debugging. If you ship a bare bones unit of functionality, you may not get
      the debugging tools needed to understand a drash.
    - Security: more tiny components, less protection from other OS facilites (which
      not execist in your tiny comptuational slice)
    - Vendor lock-in : 
          - But in the serveless world, no OS abstraction between comptuation and support
        environment
        - So not "write once, run everywhre" 
    - Configuration: can't make _any_ assumptions about background utilities from
      "the operating system" cause their ain't one
      - You have to do it all.


## Containers and Virtual Machines


If iterators is small abstraction
- and OS is large abstraction
- then containers are in the middle


<img src="https://imesh.github.io/images/contvsvm.png">


## UNIX


If iterators and error handlers are "little abstractions", then operating systems are
"big abstractions".


<img align=right width=500 src="https://upload.wikimedia.org/wikipedia/commons/4/49/Baby_Bells.svg">


- Pre-unix: operating systems were hardware-specific
- The breakup of the Bell System was mandated on January 8, 1982
  - So after laying down all that copper
    - Bell Corporation was not allowed to use it all. 
    - And they actually set up commercial competitors!
- They needed someway for different organizations to work together
  - The ultimate "why can't we all get along"
- Step1: a hardware independent systems language "C"
- Step2: an operating system written in "C"
- Step3: design patterns to allow for interactions
  - Uniform file representation (everything is "ASCII test", no special binary formats for each fie).
  - Use pipes


# Programming Languages and Abstraction


## LISP: The Ultimate Abstraction


Consider a minimal programming language with just a few primitives, plus a macro
language for assembling those primitives into more complex reasoning.
- Build mappings from primitives down to hardware
  - Port those  small number of mappings to many platform
- Let programmers work up from the primitives.


Enter LISP:


<img src="https://imgs.xkcd.com/comics/lisp_cycles.png">


[LISP](https://www.youtube.com/watch?v=HM1Zb3xmvMc), its the source


- 1955: LISP: a minimal virtual machine. Code these (small set of primitives) on any hardware
  you like then, on top of all that, code written in LISP runs everywhere


(Aside:   Well, not really. 
- Turns out, code does more than "computes". 
  - It also "connects" (to GUIs, databases, networks)
  - It also "explores"; i.e. Cognitive support for humans  
    exploring the world with software.
- But we'll get back to that.)


[Paul Graham](http://www.paulgraham.com/rootsoflisp.html)
  - "In 1960, John McCarthy published a remarkable paper in which he did for programming something like what Euclid did for geometry. He showed how, given a handful of simple operators and a notation for functions, you can build a whole programming language. He called this language Lisp, for "List Processing," because one of his key ideas was to use a simple data structure called a list for both code and data."
- [Do not read](https://web.archive.org/web/20131004232653/http://www-formal.stanford.edu/jmc/recursive.pdf)
  MacCarthy, 1960, "Recursive Functions of Symbolic Expressions and Their Computation by Machine, Part I"
- Here's a [Better](https://sep.yimg.com/ty/cdn/paulgraham/jmc.ps?t=1595850613&) read


Here's a LISP interpreter written in LISP:


```lisp
; The Lisp defined in McCarthy's 1960 paper, translated into CL.
; Assumes only quote, atom, eq, cons, car, cdr, cond.
; Bug reports to lispcode@paulgraham.com.


(defun null. (x)
  (eq x '()))


(defun and. (x y)
  (cond (x (cond (y 't) ('t '())))
        ('t '())))


(defun not. (x)
  (cond (x '())
        ('t 't)))


(defun append. (x y)
  (cond ((null. x) y)
        ('t (cons (car x) (append. (cdr x) y)))))


(defun list. (x y)
  (cons x (cons y '())))


(defun pair. (x y)
  (cond ((and. (null. x) (null. y)) '())
        ((and. (not. (atom x)) (not. (atom y)))
         (cons (list. (car x) (car y))
               (pair. (cdr x) (cdr y))))))


(defun assoc. (x y)
  (cond ((eq (caar y) x) (cadar y))
        ('t (assoc. x (cdr y)))))


(defun eval. (e a)
  (cond
    ((atom e) (assoc. e a))
    ((atom (car e))
     (cond
       ((eq (car e) 'quote) (cadr e))
       ((eq (car e) 'atom)  (atom   (eval. (cadr e) a)))
       ((eq (car e) 'eq)    (eq     (eval. (cadr e) a)
                                    (eval. (caddr e) a)))
       ((eq (car e) 'car)   (car    (eval. (cadr e) a)))
       ((eq (car e) 'cdr)   (cdr    (eval. (cadr e) a)))
       ((eq (car e) 'cons)  (cons   (eval. (cadr e) a)
                                    (eval. (caddr e) a)))
       ((eq (car e) 'cond)  (evcon. (cdr e) a))
       ('t (eval. (cons (assoc. (car e) a)
                        (cdr e))
                  a))))
    ((eq (caar e) 'label)
     (eval. (cons (caddar e) (cdr e))
            (cons (list. (cadar e) (car e)) a)))
    ((eq (caar e) 'lambda)
     (eval. (caddar e)
            (append. (pair. (cadar e) (evlis. (cdr e) a))
                     a)))))


(defun evcon. (c a)
  (cond ((eval. (caar c) a)
         (eval. (cadar c) a))
        ('t (evcon. (cdr c) a))))


(defun evlis. (m a)
  (cond ((null. m) '())
        ('t (cons (eval.  (car m) a)
                  (evlis. (cdr m) a)))))
```


- Here's a [much, much better](https://norvig.com/lispy.html)
  - Sooo much fun
- Lisp = computation = rewrite terms
    - there are atoms (symbols, numbers or nil or `t`, aka "true")
    - and there are lists (which contain atoms of lists)
    - 'a ==> a
    - `(eq x y)` is the same or both nil
      - `(car '(a b c))` ==> `a` ; i.e. pull the head
      - `(cdr '(a b c))` ==> `(b c)` ; i.e. pull the rest
    - `(cons 'x '(y z))` ==> `(x y z)` ; i.e. assemble something
    - `(cond (if1 do1) (if2 do2) ..)`  ; i.e. branch the reasoning
  - "Functions" and _lambda bodies_ `((lambda (p1 p2 p3..) e)  a1 a2 a3...)`
    - set `p1 p2 p3...` to the values of the arguments `a1 a2 a3...`
    - then evaluate  `e`.
    - Note that lambda bodies are just lists (so we can build them up and pull them down with `car` `cdr` `cons` just
      like anything ese
    - When we "define a function", we add a "lambda body" to the  "environment"
  - "Environments" and lists of pairs of symbol binding
    - `'((a 1) (b 2) ...)`
    - When enter a lambda body, we add parameter arguments to the _left_ hand side:
      -  `((p1 a1) (p2 a2) (p3 a3) (a 1) (b 2) ...)`
      - Look up local values left to right, local recursive vars shadow parent vars
        - So now we can recursion.


```lisp
is.py> (define circle-area (lambda (r) (* pi (* r r))))
lis.py> (circle-area 3)
28.274333877
lis.py> (define fact (lambda (n) 
              (if (<= n 1) 
            1 
      (* n 
         (fact (- n 1))))))
lis.py> (fact 10)
3628800
lis.py> (fact 100)
9332621544394415268169923885626670049071596826438162146859296389521759999322991
5608941463976156518286253697920827223758251185210916864000000000000000000000000
lis.py> (circle-area (fact 10))
4.1369087198e+13
lis.py> (define first car)
lis.py> (define rest cdr)
lis.py> (define count (lambda (item L) 
            (if L 
                (+ (equal? item (first L)) 
                   (count  item (rest L))) 
                0)))
lis.py> (count 0 (list 0 1 2 3 0 0))
3
lis.py> (count (quote the) (quote (the more the merrier the bigger the better)))
4
lis.py> (define twice (lambda (x) (* 2 x)))
lis.py> (twice 5)
10
lis.py> (define repeat (lambda (f) 
                          (lambda (x) 
                              (f (f x)))))
lis.py> ((repeat twice) 10)
40
lis.py> ((repeat (repeat twice)) 10)
160
lis.py> ((repeat (repeat (repeat twice))) 10)
2560
lis.py> ((repeat (repeat (repeat (repeat twice)))) 10)
655360
lis.py> (pow 2 16)
65536.0
lis.py> (define fib (lambda (n) 
               (if (< n 2)
                   1 
                  (+ (fib (- n 1)) 
                     (fib (- n 2))))))
lis.py> (define range (lambda (a b) 
                           (if (= a b) 
                               (quote ()) 
                               (cons a 
                                     (range (+ a 1) 
                                            b)))))
lis.py> (range 0 10)
(0 1 2 3 4 5 6 7 8 9)
lis.py> (map fib (range 0 10))
(1 1 2 3 5 8 13 21 34 55)
lis.py> (map fib (range 0 20))
(1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597 2584 4181 6765)
```  


LISP was crazy popular and remains very influential
- And LISP ideas are constantly being added to other programming languages
  - Paul Graham: 
    "It's worth understanding what McCarthy discovered, 
    not just as a landmark in the history of computers, but as a 
      model for what programming is tending to become in our own time. 
    It seems to me that there have been two really clean, consistent models of programming so far: the C model and the Lisp model. These two seem points of high ground, with swampy lowlands between them. As computers have grown more powerful, the new languages being developed have been moving steadily toward the Lisp model. A popular recipe for new programming languages in the past 20 years has been to take the C model of computing and add to it, piecemeal, parts taken from the Lisp model, like runtime typing and garbage collection."
- Not until Julia, did I ever see a macro system as good as 
  that in LISP.
- And what about multi-methods?


```lisp
;;; numeric columns -----------------------------
(defmethod add1 ((self num) (x string)) 
  "Handling strings from text files 
   where 'x' is not a number yet."
  (add1 self (read-from-string x)))


(defmethod add1 ((self num) (x number))
  "Knuth's algorithm for incrementally 
   updating lo, hi, mu, sd."
  (with-slots (n mu m2 hi lo sd) self
    (let ((d (- x mu)))
      (if (> x hi) (setf hi x))
      (if (< x lo) (setf lo x))
      (incf mu (float (/ d n)))
      (incf m2 (float (* d (- x mu))))
      (setf sd 
            (cond ((< m2 0) 0)
                  ((< n 2) 0)
                  (t (sqrt (/ m2 (- n 1))))))))
  x)
```


Vendor wars killed LISP
- When Peter Norvig went to Google, he had to recommend  
  Python, not LISP, since even  decades after its invention 
  there was still no platform independent GUI.
- Still, for a good time, install SBCL and have fun


## JavaScript


- ECMA
  - In September 1995, a Netscape programmer named Brandan Eich developed a new scripting language in just 10 days. 
    - Clinet-side intra-interpreter language
      - a Virual machine in every borwser
    - Why so fast? Cause its theoretical foundations were well defined... in LISP.
  - It was originally named Mocha, but quickly became known as LiveScript and, later, JavaScript.


- ERLANG, ELIXR


## Transpilers


- Transpilers
  - Why write a new language? Why not just convert your source code into some other language
    - e.g. CoffeeScript into JavaScript


<img src="https://raw.githubusercontent.com/txt/se20/master/etc/img/cs.png">


But problem with transpliers: where are the line numbers?


## Smalltalk


<img align=right width=500
 src="https://lh3.googleusercontent.com/-ezZ4lM0y5rE/WezC7wsnC2I/AAAAAAABFgc/3NuHmtD8q20B11eRKpL141huA2nC5JnpQCHMYBhgL/w606/smalltalk-desktop.jpg">


- 1974 Smalltalk VM
  - Its the source man
  - Invented bit-mapped graphics, multi-windows environment,
    pure OO prorgramming
  - Significantly advanced the art of garbage collection, virtual machines
  - [Smalltalk-80 in a TV show](https://www.youtube.com/watch?v=AuXCc7WSczM)
  - [Smalltalk article 1980](http://dreammachin.es/Kay_SciAm_77.pdf)
  - Later on, was used to design the Java VM 
    - Q: Why does JAVA have single parent inheritance? 
    - A: Cause of Smalltalk


Smalltalk class hierarchy (somewhere in the 1980s):


<img align=right src="https://i.pinimg.com/originals/e2/c1/4a/e2c14a7f83ea042e9dc8e0031e5e1a72.jpg">


```
Object
|    Behavior
|    |    ClassDescription
|    |    |    Class
|    |    |    Metaclass
|    BlockClosure
|    Boolean
|    |    False
|    |    True
|    Browser
|    Collection
|    |    Bag
|    |    MappedCollection
|    |    SequenceableCollection
|    |    |    ArrayedCollection
|    |    |    |    Array
|    |    |    |    ByteArray
|    |    |    |    WordArray
|    |    |    |    LargeArrayedCollection
|    |    |    |    |    LargeArray
|    |    |    |    |    LargeByteArray
|    |    |    |    |    LargeWordArray
|    |    |    |    CompiledCode
|    |    |    |    |    CompiledMethod
|    |    |    |    |    CompiledBlock
|    |    |    |    Interval
|    |    |    |    CharacterArray
|    |    |    |    |    String
|    |    |    |    |    |    Symbol
|    |    |    LinkedList
|    |    |    |    Semaphore
|    |    |    OrderedCollection
|    |    |    |    RunArray
|    |    |    |    SortedCollection
|    |    HashedCollection
|    |    |    Dictionary
|    |    |    |    IdentityDictionary
|    |    |    |    |    MethodDictionary
|    |    |    |    RootNamespace
|    |    |    |    |    Namespace
|    |    |    |    |    SystemDictionary
|    |    |    Set
|    |    |    |    IdentitySet
|    ContextPart
|    |    BlockContext
|    |    MethodContext
|    File
|    |    Directory
|    FileSegment
|    Link
|    |    Process
|    |    SymLink
|    Magnitude
|    |    Association
|    |    Character
|    |    Date
|    |    LargeArraySubpart
|    |    Number
|    |    |    Float
|    |    |    Fraction
|    |    |    Integer
|    |    |    |    LargeInteger
|    |    |    |    |    LargeNegativeInteger
|    |    |    |    |    LargePositiveInteger
|    |    |    |    |    |    LargeZeroInteger
|    |    |    |    SmallInteger
|    |    Time
|    Memory
|    Message
|    |    DirectedMessage
|    MethodInfo
|    Point
|    ProcessorScheduler
|    Rectangle
|    Signal
|    |    Exception
|    |    |    Error
|    |    |    |    Halt
|    |    |    |    |    ArithmeticError
|    |    |    |    |    |    ZeroDivide
|    |    |    |    |    MessageNotUnderstood
|    |    |    |    UserBreak
|    |    |    Notification
|    |    |    |    Warning
|    Stream
|    |    ObjectDumper
|    |    PositionableStream
|    |    |    ReadStream
|    |    |    WriteStream
|    |    |    |    ReadWriteStream
|    |    |    |    |    ByteStream
|    |    |    |    |    |    FileStream
|    |    Random
|    |    TextCollector
|    |    TokenStream
|    UndefinedObject
|    ValueAdaptor
|    |    NullValueHolder
|    |    PluggableAdaptor
|    |    |    DelayedAdaptor
|    |    ValueHolder
```


