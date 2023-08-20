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
  






## SE: the times they are a changin'


_Some notes on the past and future of SE_


Once upon a time:


-  "users" were considered to be outside of the scope of SE. 
     - “The notion of user cannot be precisely defined  and therefore has no place in CS or SE” -- Dijkstra, ICSE4, 79
     - And then ...
- "compiling" was considered not safe practice for programmers 
     - See "cleanrooms" and Harlan Mills, 1985. 
     - And then ...
- "requirements" was not an SE prolem.
     - "Analysis and allocation of the system requirements is NOT the responsibility of the SE group but is a prerequisite for their work”. -- Paulk, 1993
     - And then ...
-  "testing" was seen as "someone else's problem" (the test team). And then ...
-  "operations" was seen as "someone else's problem" (the field engineers and the maintaince team). And then ...
-  "AI" was seen as separate to SE. And then ...


See other trends, below:


- Warning the following timeline might be wrong 
&plusmn; 5 years.
- Also if some trend is  big  in one decade,
  - then you know that was the result
of years of prior engineering.


## 1950s: Working it out from  Scratch


 <a href="https://www.amazon.com/dp/B005IEGK5C/ref=dp-kindle-redirect?_encoding=UTF8&btkr=1">Turing's Cathederal</a>


- Computers and atomic bombs were invented at the same time, by the same people, for the same reasons.
- We live today inside their hastily (but brilliantly) conceived design assumptions.


<img width=500 src="https://cdn.thenewstack.io/media/2020/10/8e6dde0b-maniac_memorytubes.jpg">


<br clear=all>


## 1960s: Scaling Up Process


1960: The mother of all abstractions (warning: amazing): [about](http://www.paulgraham.com/rootsoflisp.html) :: [in python](https://norvig.com/lispy.html)


-  "As computers have grown more powerful, 
   the new languages being developed have been moving steadily toward the 'Lisp' model. 
   A popular recipe for new programming languages in the past 20 years has been to take the 'C'; model of computing and add to it, piecemeal, 
   parts taken from the 'Lisp' model, like runtime typing and garbage collection."   
   -- Paul Graham


1968: The Mother of All Demos (warning: long) [about](https://en.wikipedia.org/wiki/The_Mother_of_All_Demos) :: [video](https://www.youtube.com/watch?v=B6rKUf9DWRI)


See also: <a href="https://en.wikipedia.org/wiki/The_Mythical_Man-Month">Mythical Man (sic) Month</a>


<img align=left width=500
src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRBumOaskOHgW-ZE_2Cg49DoKuf0y3qwG6jNA&usqp=CAU">


"For some years I have been successfully 
using the following rule of thumb for 
scheduling a software task:


- l/3 planning
- l/6 coding
- l/4 component test and early system test 
-  l/4 system test, all components in hand."


Pay attention: half of development is testing.


<br clear=all>


## 1970s: Personnel


Alan Kay: the best way to predict the future is to invent it.


- If you want to see what he meant: [Microelectronics and the Personal Computer](http://mnielsen.github.io/notes/kay/micro.pdf) Alan C. Kay Scientific
American Vol. 237, No. 3 (September 1977), pp. 230-245


<img width="680" alt="image" src="https://user-images.githubusercontent.com/29195/129641843-1cb3cead-6aa8-4b4f-9bd1-69d8fa617a8d.png">


"The user makes his primary input through a typewriter like keyboard
and a pointing device called a mouse which controls the position
of an arrow on the screen."


"WINDOWS" display frames within the  larger display screen, enabling
the user to organize  and  edit information at several levels  of
refinement.


<br clear=all>


## 1980s: Scaling up the Hardware


<a href="https://en.wikipedia.org/wiki/Halt_and_Catch_Fire_(TV_series)"> Halt and Catch Fire</a>


<br clear=all>


## 1990s: Connections (Welcome to the Internet)


- Internet, 
- Open Source; e.g. see 
  [Shares of Linux Firm Red Hat More Than Triple After IPO](https://www.wsj.com/articles/SB934376738897331391)
- [Internet Bubble](https://corporatefinanceinstitute.com/resources/knowledge/trading-investing/dotcom-bubble/):
  1995 to 2001, massive price rises in Internet  stocks. Then...
  - "The bursting of the bubble caused market panic through massive 
      sell-offs of dotcom company stocks, driving their values further down, 
    and by 2002, investor losses were estimated at around $5 trillion." 


<br clear=all>


## 2000: Social


<a href="https://en.wikipedia.org/wiki/The_Social_Network">The Social Network</a>


<br clear=all>


## 2010: Mobile, Cloud


Welcome to the [attention economy](https://en.wikipedia.org/wiki/Attention_economy).
- The age is (myth)misinformation. Information, weaponized.


Cloud 
- (Some history)[https://www.dataversity.net/brief-history-cloud-computing/]


![cloud](/etc/img/cloud.png)


## 2020: AI


### AI 


Autonomous vehicles.


AI-driven Development Is Here: 
[Should you worry?](/etc/pdf/AI-Driven_Development_Is_Here_Should_You_Worry.pdf)
e.g. you type:


```
# import a file named“observations.csv”
# and print the number of rows and columns
# then use the data to create
# a plot of the observations
```
and Github's copilot tool reponds woth


```python
data = []
with open(‘observations.csv’) as csvfile:
 reader = csv.reader(csvfile)
 for row in reader:
   data.append(float(row[0]))
 print(“Number of rows: ,” len(data))
 print(“Number of columns: ,” len(data[0]))
 plt.plot(data)
 plt.show()
```


Warning: this code is learned from 159 Gb   of code from Github. So this is very much **average code** with the average number of bad ideas and secutiry holes. 


### ?? Blockchain


er... what can we say about blockchain? well...


- Aug 12, 2021: Ezra Klein, NY Times:
  - If the original internet let you easily copy information, 
    the next internet will let you easily trade ownership of digital goods. 
  - Crypto lets you make digital goods scarce, which increases their value; 
    it lets you prove ownership, which allows you to buy and sell them; 
    and it makes digital identities verifiable, as that’s merely information you own
  - Together, they unlock the potential for a true economy for digital goods, 
    where creators actually get rewarded for what they make. I will admit to some skepticism that this is how it’ll play out, 
    as many of the financiers funding crypto also founded and sit on the boards of the companies that set the terms of today’s internet, but we’ll see.
 - Jun 29, 2022:
    - [Crypto crisis: how digital currencies went from boom to collapse](https://www.theguardian.com/technology/2022/jun/29/crypto-crisis-digital-currencies-boom-collapse-bitcoin-terra)


## Present day


### Q: Which language is best?


A: none of them.
<img width=900 src="https://github.com/txt/se20/blob/master/etc/img/tiobe.png">


And the language you use next is probably not the one you are using now:


- Empirical Analysis of Programming Language Adoption Leo A. Meyerovich, Ariel Rabkin, OOPSLA ’13.


<img width=700 src="https://github.com/txt/se20/blob/master/etc/img/nextLanguage.png">


And even if you are working on some language/tool now, if your work changes, that
could change too


<img width=700 
 src="https://github.com/txt/se20/blob/master/etc/img/groups.png">


### Q: So How many languages will you need to know?


Projects are build from  2-5 Programming Languages 


- Mayer, Philip, and Alexander Bauer. "An empirical analysis of the utilization of multiple programming languages in open source projects." 
   Proceedings of the 19th International Conference on Evaluation and Assessment in Software Engineering. 2015.
-  Tomassetti, Federico, and Marco Torchiano. "An empirical assessment of polyglot-ism in github." Proceedings of the 18th International Conference on Evaluation and Assessment in Software Engineering. 2014.


An average engineer routinely uses 7 PLs:


-  Mayer, Philip, Michael Kirsch, and Minh Anh Le. "On multi-language software development, 
   cross-language links and accompanying tools: a survey of professional software developers." Journal of Software Engineering Research and Development 5.1 (2017): 1.


How to learn so many languages:


- Cross-language self-tutoring
- If you can do X in language1, find out how to do X in language2;
- Jean Scholtz and Susan Wiedenbeck. 1990. Learning second and subsequent programming languages: A problem of transfer. International Journal of Human-Computer Interaction 2, 1 (1990), 51–72. 
- N. Shrestha, T. Barik, and C. Parnin. 2018. It’s Like Python But: Towards Supporting Transfer of Programming Language Knowledge. In 2018 IEEE Symposium on Visual Languages and Human-Centric Computing (VL/HCC). 177–185.


### Q: Is programming the same as software engineering?


Programmers don't just program:


- [Tom Zimmermann, Microsoft](https://www.microsoft.com/en-us/research/podcast/the-productive-software-engineer-with-dr-tom-zimmermann/)
-  If you think of a typical software engineer at Microsoft, they spend about half of a day on development related activities, 
     and the other half of the day is spent on other activities like coordinating with other people in meetings, sending emails.... So, 
    there’s actually not that much time that they can spend on writing code, and the time they spend writing code, on a good day, it’s actually 
     only 96 minutes, and on a bad day it’s, on average, 66 minutes. And half an hour writing code actually can make the difference between a bad and a good workday.


What else do "programmers" do:


- Convincing you that the system is trustable
- Helping you when the systems fails


Current roles of software engineering experts 
when adopting data mining approaches:


- Problem definition.
- Data collection.
- Data “surrogates” (when the joins fail you)
- Model building.
- Managing organizational impact
  - MINKU, L.L.; MENDES, E.; TURHAN, B. . "Data Mining for SE  and Humans in the Loop", Progress in Artificial Intelligence (PRAI), 5(4), 307-314, Nov  2016


Programmers are the people who know when not to program:


- Exhibit A: Ken Thompson, of Unix and C fame, once said "One of my most productive days was throwing away 1000 lines of code."
- Exhibit B: programmers know that not all openned issues should be closed


![](/etc/img/ratio.png)


