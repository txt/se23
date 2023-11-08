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
  






# Patterns
  
 If you want someone to understand something new, build it out of old stuff that they have seen before.
  
- Express it in terms of  a pattern that experienced programmers already might know something about.
- Experts glance at things and see patterns missed by novices
  - When experts talk, they talk in patterns.
  - To document better, talk patterns 


![image](https://user-images.githubusercontent.com/29195/132730127-41488a53-a17a-438d-b120-0534797f6795.png)


  
  Q: So what have programmers seen before that might repeat in future systems?    
  A: Patterns
  - e.g. _idioms_ : small code-level patterns 
  - e.g. _design patterns_: common collections of a few classes
  - e.g. _archtirctures_: recurring "big picture" structures seen in large systems


## Example 1: 3-tiered architectures
  
Data : model : dialog
- Data = ? SQL
- Model = ? some object system
- Dialog = ? some gui tool


![image](https://user-images.githubusercontent.com/29195/132729813-e4ff6bb9-51e7-4985-a005-fc05b70362de.png)


- The power of patterns
  - Patterns come with review heuristics
  - Which can identify problems... which can be solved ... using other patterns.
  - So patterns take us naturally to design review/ critique/ improvement


- Problem: data and dialog both need the same constraint info (e.g. 0 <= age <= 120): Where to store it?
  - A solution: Ruby on Rails, DRY: “don’t repeat yourself”
    - Database and Web-GUi generated  from a class model 
    - Simplified (amazing) last decade’s web designs
    - Each web url has actually a method on a class
  - A very popular solution (until we went much more "REST" ful)
 
![image](https://user-images.githubusercontent.com/29195/132729905-53b58504-3ed8-425b-99f4-9a326043360d.png)


## Example 2: Composite design patterns


![image](https://user-images.githubusercontent.com/29195/132732186-f1aeec90-3d7c-4890-affc-61a0b2d376dc.png)


	
  ![image](https://user-images.githubusercontent.com/29195/132730145-249b070f-5779-4d0d-b5a5-575a8160e74d.png)


  ![image](https://user-images.githubusercontent.com/29195/132730161-7cdc5972-5870-48b2-8583-79ae3821b533.png)


  ![image](https://user-images.githubusercontent.com/29195/132730271-1d4248a2-0137-4e17-9fc4-789044e73056.png)


Patterns have review heuristics:


  - E.g. delete cascade?  in composites 
	  - If “it” gets deleted, then do you delete the sub-parts


 ## Example 3: Blackboard Architectures
  
Collaborative problem solving


 ![image](https://user-images.githubusercontent.com/29195/132730595-14e6fdea-e41b-40a3-aec0-357b9d71e1c6.png)
 
 Layered feature extraction: agents read from level[i], write to level [i+2]


  
 ![image](https://user-images.githubusercontent.com/29195/132730620-465dc0ae-18b2-45da-b4fc-4914cce5dc71.png)
 
 ![image](https://user-images.githubusercontent.com/29195/132730653-e140d018-fc0e-4e57-baf7-f3ea4b67f6ab.png)


  Each agent has rules if &lt;condition> then  &lt;action>  
  
  ![image](https://user-images.githubusercontent.com/29195/132730926-67350126-1bc6-4f77-a557-64ad1d2c8c3a.png)


Patterns have review heursitcs:
  
- No “best” answers, but issues that experts expect to debate  
- Issue #1: systems issues: how to get everyone onto the net?-
- Issues #2: network intera lingue. How to share?
- Issue #3: Schedule. How to pool the different agents?
- Issue #4: Conflict resolution. What to do when 2 agents have satisfied conditions?


## Example 4: Layers
  
- Blackboards a kind of layered architecture
- Code at level[X] only talks to levels[X+1], levels[X-1] 
  - Via well-defined interfaces
- Layer[X] can be pull out and easily replaced
  - Just as long as new layer[X] maintains the same interface
- Low-level issues can be abstracted away to higher levels
- Separation of concerns at different layers
- E.g. OSI Network layers architecture: 
  - “The purpose of the OSI reference model is to guide vendors and developers so the digital communication products and software programs they     
     create will interoperate, and to facilitate clear comparisons among communications tools.”
- E.g. LAMP, ISO network model
  
![image](https://user-images.githubusercontent.com/29195/132731131-093cceaf-582f-4fd4-82d7-6c9c34850845.png)


![image](https://user-images.githubusercontent.com/29195/132731193-4f473bd6-4d8c-4f32-975e-de5d24f7b846.png)


 Patterns have review heursitics:
  
- Implementation complexity
- Slow (messages have to navigate many layers)
- Internal barries to change
  
Mean: a fix to removing internal barries to change in layerd patterns
  
-  M = MongoDB:  a non-SQL DB  (nested key-value pairs) 
- E = Express.js : controller layer,  directing application flow and marshaling data.
- A = AngularJS : handles data presentation. 
- N = Node.js: an extensive javascript library (look ma, no operating system) 
- MEAN: one language up and down the stack (Javascript)
  - faster integrated testing; 
  - faster invention of new patterns.
  
![image](https://user-images.githubusercontent.com/29195/132731515-82b9842f-5114-4c1f-88d7-18d33b191287.png)


 ## Example4: Layers at the Dept of Defence Software
  
Doug Schmidt:
- Architectural Evolution of  
DoD Combat Systems
Doug Schmidt, 
SEI blog, 
Nov 15, 2013
- "The Department of 
Defense (DoD) must 
move away from 
stove-piped solutions:
- "... towards a few technical reference frameworks ..."
-  "based on reusable hardware & software services"


![image](https://user-images.githubusercontent.com/29195/132731317-97f48837-b9f0-4052-af41-8fd3a168a34b.png)


## Example 5: CRUD: low-level code idiom
	
CRUD = create, read, update, delete
	
- In  SQL:  INSERT = C, SELECT = R , UPDATE and DELETE.
- In http:  : GET = R, DELETE.= D, PUT=?, POST=? 
  - PUT : might create  new user or update info on an existing user (so PUT  = C or U?)
  - POST :  sends data to the server and leaves it up to the server to do something with it  


CRUD2 (a timm special)
- CRUD + search  + zoombie (a proxy that  cannot be committed (inserted) used)
- For GUI constrain info 


	
BTW, CRUD can leap from idiom to architecture (web-scale RESTful applications)
	
Regardless
- the main points here is
that complex systems can be abstracted 
into reasonable chunks via Patterns
- Such abstraction simplifies how we discuss even complex
systems
	
## For more on Patterns
	
![image](https://user-images.githubusercontent.com/29195/132732089-6dbbd7c3-53f0-4a6a-a51b-b088d409d384.png)


[Design Patterns: Elements Of Reusable Object-Oriented Software](https://www.biblio.com/9780201633610) (1995) 
- The “Gang of 4” (GOF) book
- 43,582 citations
- 500,000 copies sold
- All codes, in ruby (very nice): https://github.com/davidgf/design-patterns-in-ruby   
-  Examples: http://asi.insa-rouen.fr/enseignement/siteUV/genie_logiciel/supports/ressources/exemples_de_la_vie_reelle_pour_illustrer_pattern.pdf  


	![image](https://user-images.githubusercontent.com/29195/132732541-c53d68c4-1f3f-4830-935e-e2f544319280.png)


- Note: something strange about GOF. 
- Misses architectural patterns 
(larger things than design patterns). E g CRUD, blackboards
- 23 patterns in 1995. Not 230 since.
  - Functional programers invent 10 patterns before lunch
     http://norvig.com/design-patterns/design-patterns.pdf
  - Peter Norvig: "Design patterns are bug reports  against your programming language.”
	


