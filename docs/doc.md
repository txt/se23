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
  






# Documentation 
## Tell me a story I can Understand
 (that makes me want to use your code)
  
 "I have made this letter longer since I did not have time to make it shorter" -- Blaise Pascal
  
- Documentation is **hard**
- [Doc generation tools](http://menzies.us/bnbad2/duo4.html) are the start, not end, of documentation
- Badges are “bling” (not documentation)


![image](https://user-images.githubusercontent.com/29195/130994411-6dffc04e-a8fd-442d-bff7-0e8ee702197b.png)


- What a great documentation (first "C" book):
  - Chapter1:
    [A modern  work of art](https://www.ccapitalia.net/descarga/docs/1978-ritchie-the-c-programming-language.pdf).


##   Example of good “why” documentation


Showcases succintly, 
- the key points
- what the thing is
- where to learn more?


e.g. [Starship](https://github.com/starship/starship)
  
![image](https://user-images.githubusercontent.com/29195/130994728-5d4c4c9d-1686-43c6-940a-6d1d475e9247.png)


## Some Documentation Generation tools'


 Lightweight (markdown):
  
  ![image](https://user-images.githubusercontent.com/29195/130996948-68d19e6e-c7ed-443f-a906-2e01e307f146.png)
 
Medium weight, highly recommended (asiidoc):


- see [asciidoclive](https://asciidoclive.com/edit/scratch/1)
 
 Heavyweight (latex):
  
  ![image](https://user-images.githubusercontent.com/29195/130997040-797ccb18-176e-41ec-9275-a53134343905.png)


(Aside: please take a moment to read the [sad, sad story about markdown's creator](https://en.wikipedia.org/wiki/Aaron_Swartz)).
  
Pdoc3: Python doc strings ⇒ markdown ⇒ web pages  
  
 <a href="https://timm.github.io/bnbad/"><img 
width=600 src="https://user-images.githubusercontent.com/29195/130997647-d933884e-8e5c-4f0c-a367-6a5d69bb1df1.png"></a>


 Trans-document documentation tools
- [Pandoc](https://pandoc.org/Pandoc)
  ![image](https://user-images.githubusercontent.com/29195/130997844-830d0381-48bb-484a-b0fb-9afb7dc358f0.png)


## Documentation words of wisdom


- Great list of pointers:
  - https://github.com/sixhobbits/technical-writing/blob/master/resources.md


- Doc should be kept under version ctonrol
  - Maybe even store your documentation in the same repository as its corresponding product source code.
    - Big win with versioned documentation
      - People can go back to the doco at that that for that version of the code. Bug win!
    - Developers are more likely to contribute if they don't have to clone a separate repository.


Etter, Andrew. Modern Technical Writing: An Introduction to Software Documentation (p. 15). Kindle Edition. 


- I have perhaps an irrational bias towards static websites. I love them. I love their speed, simplicity, portability, and security. You can host static websites practically anywhere, including Amazon S3 and GitHub Pages. They have no server-side application dependencies, no databases, and nothing to install, so migrating the entire site is as easy as moving a directory.


- Doc should answer 4 questions:
  - What is this product? Why would anyone want it?
  - How does this product fit into a broader ecosystem, if at all? Does it have any dependencies?
  - Where can I acquire this product? If there are multiple distribution packages, which should I choose and why?
  - How do I install the product? What are the basic configuration options, if any?
  - What does a simple, start to finish operation look like?
    - Some e.g.  pictorial walkthrough to a functional code sample
- Bias towards including headers, tables, lists, diagrams, and images. 
  - These additions make your writing more approachable and simpler to scan than 
    paragraph after paragraph of prose.
- Dont use wikis (if you even remember them) 
  "In short, for a wiki to make sense, your documentation should
  be uncontroversial and never need to be versioned. You also
  shouldn't mind writing in an inferior editor, only working online,
  and maintaining a piece of enterprise software."
- Don't use MS Word
  - "Microsoft Word is a wonderful choice for creating résumés and a
     horrible choice for creating documentation.
  -  "Its lone purpose in
     this world—one that, again, it really does perform admirably- is
     to create short, attractive PDFs that people can read and discard.
  -  "Documentation with any sort of lifespan needs to be kept in version
     control, which Word's DOCX file format (a compressed collection
      of XML files) actively opposes. 
  -  "Documentation should live online,
     and Word's HTML export is totally unsuitable for creating
     websites."
- WRONG: Technical writers produce comprehensive documentation.
  - RIGHT: Writing should be the minimum possible length. 
    Huge blocks of writing look intimidating, and excessive content
    waters down useful content. Identify what the audience actually
    needs to know, and include only that.
- If you aren't keeping an eye on documentation metrics, you're making a huge mistake. 
  User research is wonderful, but knowing exactly which pages are most popular, your site's 
   bounce rate, and common behavioral flows are all invaluable.
- Pandoc is a marvelous tool for converting between markup formats. It calls itself the 
  Swiss Army knife of markup converters and can convert to and from a huge number of formats.
   Unfortunately, these conversions are rarely perfect. If one day you decide that you'd rather 
  write in AsciiDoc instead of Markdown, expect to perform some manual cleanup after 
  running the conversion script.


## So that's it? The Documenation Problem is Solved?
  
Not really
  
None of these tools solve the documentation problem
  
Kinds of doc (hint: "why not"; rarer than "why"; rarer than "how"; rarer than "what"):


- What : point description 
  - e.g. UML, 
  - e.g. what pdoc3 generates 
- How: common use cases
  - See [The scikit-learn doco](https://scikit-learn.org/stable/) (exploding with examples)
  - See [last third of “PCL”[(https://gigamonkeys.com/book/)
- Why: top-level motivation
  - See Meyer’s OO software construction [Chapter1](https://web.uettaxila.edu.pk/CMS/AUT2011/seSCbs/tutorial/Object%20Oriented%20Software%20Construction.pdf) says nothing about objects
  - See [“Data mining from scratch”](http://math.ecnu.edu.cn/~lfzhou/seminar/[Joel_Grus]_Data_Science_from_Scratch_First_Princ.pdf) (Joel Grus) 
- Why-not: choices within the design
  - Path not travelled


 For a sensational case study, read the original textbook on "C". 
  - [Chapter1](http://www.ccapitalia.net/descarga/docs/1978-ritchie-the-c-programming-language.pdf) is a work of art
 
  
## If you want to reap the benefits of good documentation 


Make the documents something reasonable 


(e.g. documentation ⇒ verification 
or documentation ⇒ code generation)


### “Why not” documentation
- e.g. Feature model: looks like “just” a pretty picture.
-  But look again: see the logic?  the constraints? the why nots
  
![image](https://user-images.githubusercontent.com/29195/130999315-28599041-7988-49a0-bd36-3af6fd8a245c.png)


- This model: 10 variables, 8 rules
- Linux kernel: 6,888 variables, 344000 rules


### “What” documentation: 
- e.g. State transition diagrams
- David Harel, Statecharts: A visual formalism for complex systems. Science of Computer Programming, 8(3):231-274, June 1987. 
10,100+ citations (!!!)
- Black dot = initial state
- Dashed lines: parallel work
- Words on arcs: transition guards
- Solid line: nested sub-state machines (and all transitions on super-states apply to sub-states)
  
  ![image](https://user-images.githubusercontent.com/29195/130999564-4965a203-83c0-46cb-b293-57a94a6d940d.png)


- Good for scriblling on white board: 
  - very good for small systems ( e.g. internal reasoning within one class )
- Good for reasoning about mission critical kernels on safety critical systems
  - Can reason over diagram to look for
    - Live locks: loops which never terminate
    - Dead locks: states we can never escape


![image](https://user-images.githubusercontent.com/29195/130999771-d6d4e927-fc0e-4cfe-8216-25c0bfaa1209.png)


### **“What”** documentation
- e.g. Entity-Relationship Diagrams
- Database design
  - Don’t document the code
  - Document the data it runs on
- Everything is tables, whose cells can be String, Number, Date, Blob (binary object), Null, etc...
  - But NOT a nested table
- If many of these things depends on many of those things
  - Add a relationship table in between
- A set of sanity checks for “bad” table design
  -  Store every datum once, and only once
  - Avoid, add/delete/update anomalies
- Many tools for auto-application generation (GUI screen 
Generation, ORMs like Entity Framework [C#], mapping to databases).


![image](https://user-images.githubusercontent.com/29195/131000060-bb703a24-2ad5-4375-a108-1bd52d166b62.png)


## Documentation ⇒  code generation
  
###  e.g. ER diagrams: screen painting tools


Interactive GUIs generated from database table design
  
  ![image](https://user-images.githubusercontent.com/29195/131000390-f043ca40-20f4-4592-946a-29b887c4a4d3.png)


  
### e.g. State transition diagrams
  
cross-compile to “C”
  
  ![image](https://user-images.githubusercontent.com/29195/131000444-08b270ac-977b-437b-8d7c-2bb6b5995fdd.png)


  ![image](https://user-images.githubusercontent.com/29195/131000462-fef5adcc-602c-4178-84ff-d8bc0c15e85c.png)


### e.g. Compartmental diagrams: Easy to code:


- _Flows_ change _stuff_ (and _stuff_ is called _Stocks_).
- _Stocks_ are real-valued variables , some entity that is 
accumulated over time by inflows and/or depleted by 
outflows.
 


 ![image](https://user-images.githubusercontent.com/29195/131000757-04597f42-c96f-40cc-804f-9876a16b00ca.png)


  ![image](https://user-images.githubusercontent.com/29195/131000808-af4e8634-baaf-47ba-a4b1-31c881d532f6.png)


- To code CM,
  - sum in + out_flows_ around each _stock_;
  - multiply that by the time tick dt
  - add the result back to the _stock_
  - e.g.  v.C += dt*(u.q - u.r) (u,v = before,now)


  ![image](https://user-images.githubusercontent.com/29195/131000841-b2ac37f9-3489-4342-be3e-a0c2c39fd850.png)


  ![image](https://user-images.githubusercontent.com/29195/131000861-5e207f38-0526-4e01-98da-372fabd3c1ea.png)


## Digression: A little trip into the land of UML


“What” documentation: 
UML = ER + procedures
- Unified modeling language
  
  ![image](https://user-images.githubusercontent.com/29195/131001293-3de8f7ed-1ce8-488b-b2fb-2e835a441715.png)


  ![image](https://user-images.githubusercontent.com/29195/131001314-f4ea547d-d6c5-4858-a7bc-9c6c76cb4e67.png)


Hints for writing class diagrams


- Don't add gets/setters to class methods
- If there is a relationship classX to classY, 
  - Don't add variables to X,Y. 
  - Instead connect them with a line and label the line.
  - E.g. Professor instructs student
- Also, consider [writing fewer classes](https://www.youtube.com/watch?v=o9pEzgHorH0)  (this one will just blow your mind).
  - e.g. Before: 10,000 LOC, 115 modules, 207 classes
    - After: Downsized to 135 LOC, 3 classes (to handle a particular application)
- Brainstorm with CRC cards
  - Class, responsibility, collaboration cards
    - Walk through specific scenarios
  - Hold the card to your chest and say “I update the X”
  - And when the responsibility feels wrong, pass it to another class


![image](https://user-images.githubusercontent.com/29195/131001997-5539a9f1-a395-4ab6-bf6e-6a432f397b76.png)


History has not been kind to UML
  
- UML = under-defined modeling language
  - Not enough semantics to support verification
- Marian Petre: "UML in practice" ICSE'13, 2013. http://oro.open.ac.uk/35805/
  - UML has been described by some as "the lingua franca of software engineering". Evidence from industry does not necessarily support such endorsements. How exactly is UML being used in industry — if it is? Interviews with 50 professional software engineers in 50 companies 


| | Number|
|--|------|
|  no UML	      |     35|
|selective	     |      11|
|auto-code gen	 |   3|
|retrofit	        |     1|
|wholehearted	   | 0|


  |Who uses what	  |     Number|
  |------|--------|
|Class diagrams	     |          7|
|Sequence diagrams 	 |      6|
|Activity diagrams	  |     6  |
|State machine diagram |   3|
|Use case diagrams	   |   1 |


  
- UML useful for 
  - A  'thought tool'
  - For communicating with stakeholders
  - For collaborative dialogs
  - As the starting point for adaptation (i.e., using a homegrown variant of the "real" notation)
- Two  ways to read Petre’14:
  - An indictment: after 20 years, UML is still mostly not used and not valued.
  - More hopefully,  parts of UML are used; the more we learn about which ones, where, why, and how, the better our chances of building something better.


