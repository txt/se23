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
  






# Analysis vs Design


## Analysis
- Asks "what is the problem?"
  - what happens in the current system?
  - what is the requirement in the new system?
- Leads to a detailed understanding of Requirement and Domain Properties
- Focuses on the way human activities are conducted


## Design
- Asks "how to build a solution?"
  - how will the new system work?
  - how can we solve the problem identified by the analysis?
- Leads to a solution to the problem
- Focuses on building technical solutions


# Software Architecture Design
  
 A software architecture defines multiple things:
- The components of a software system
- How the components use each other's functionality and data
- How control is managed between the components


## Client-Server architecture
  


![image](https://www.simplilearn.com/ice9/free_resources_article_thumb/Client_Server_Architecture_1.png)


- Servers provide some kind of service.
- Applications are run locally by the end user
  - (e.g: Running on local machines, and mobile devices)
- Data storage and management is treated as a server.
  - Consistency checking is located on the server
- Advantages: 
  - Breaks the system into manageable components
  - Makes control and data persistence clearer
  
But here are we talking about logical or physical architecture? Well both but with a larger focus on logical architecture.


## Coupling and Cohesion


- When designing architectures we usually think about basic building blocks:
  - Modules: which are self contained functionalities
  - Connectors: Interfaces that connect different modules 
- A good architecture will generally **minimize** coupling between modules and **maximize** the cohesion of each module


- This makes it easier for future changes and maintenance to code, as well as making the modules easier to understand.


![image](https://upload.wikimedia.org/wikipedia/commons/thumb/0/09/CouplingVsCohesion.svg/1200px-CouplingVsCohesion.svg.png)


## Pipe-and-filter architecture
![image](https://www.dossier-andreas.net/software_architecture/pipe_and_filter_3.jpg)


- Used in UNIX shell commands
- Compilers:
  - Lexical analysis -> parsing -> semantic analysis -> code generation
  - Signal Processing


### Interesting properties
- Filters do not need to know anything about what they are connected to
- Filters can be implemented in parallel
- Behavior of the system is the composition of the individual behaviors of the filters


## Event based architecture
![image](https://www.oreilly.com/library/view/software-architecture-patterns/9781491971437/assets/sapr_0201.png)


- Used in conjunction with DDD and Microsservices architecture for most real world applications, also very useful for debugging systems, for database management systems, and GUIs


### Interesting properties
- Anouncers of events don't need to know who will handle the event
- Supports re-use, and enhancement of the system


### Disadvantages
- Components have no control over order of computations


## Layered architecture (e.g: Domain Driven Design)


![image](https://blob.jacobsdata.com/software-alchemy/entry8/clean-domain-driven-design-jacobs-layer-interactions-510.png)


- Used in most real world applications, also used to develop operating systems and communication protocols


### Interesting properties
- Support increasign levels of abstraction during design
- Support enhancement and re-use
- Can define standard layer interfaces (think pipe-and-filter)


### Disadvantages
- May be hard to identify clean layers
- Without further architectural transformations tends towards a monolithic architecture.


### Open vs Closed Layered architecture


#### Open
- A layer can use services from any layer below it
- More compact code, as the services of lower layers can be accessed directly
- Breaks the encapsulation of layers, so it increases dependencies between layers


#### Closed
- Each layer only uses services of the layer immediately below
- Minimizes dependencies between layers and reduces the impact of a change


## CQRS DDD architecture
![image](https://martinfowler.com/bliki/images/cqrs/cqrs.png)


CQRS stands for **Command Query Responsibility Segregation** the concept was first introduced as an idea to separate into different modules actions that alter persisted data, and simple queries that retrieve persisted data.


### Why is it useful?
When developing systems on the modern distributed era: 
- individual modules are deployed in separate machines
- connectors are deployed as event queues (Think event based architecture)


As such, the persisted data may often come from different asynchronous sources. And when retrieving data (for the majority of cases), it is acceptable to have non atomic information.


With that in mind reading data becomes a very different process than the rest from CRUD (Create, Update, Delete). 


### Interesting properties
- Reads and Writes are considered wildly different actions in CQRS allowing for validations to work in completely different manners from a traditional DDD system.
- Allows for an easier time when moving the application from local hosting to cloud hosting.


### Disadvantages
- Many applications are not complex enough to justify the extra work required with CQRS
- Needs to be deployed together with an event based architecture


# From On-Prem to Cloud


![image](https://miro.medium.com/max/1192/1*6KH0Kt-Vh_iopiiKj3oBjQ.png)


With the advent of cloud technologies and current the high availability of low cost cloud services the architectural landscape went through changes.


Most of the applications were originally of a **monolithic** nature, which means that a server (physical machine) would contain all layers, all API's, all database access, all authorization services contained within the same process. 


The problem with this approach, is that in real life, not all services and features of a system require the same computational resources, and for many services the features that require computational resources at high demand vary over time.


So there is a very large cost with providing a cloud environment capable of serving sufficient users in a scalable and financially conscious manner.


As such the concept of **microservices** appeared. To transform any architecture cited above in microsservices we have to break down and achieve a very high level of low coupling and high cohesion, so that you can break down separate modules of the application and deploy them separetely as microsservices.


![image](https://images.edrawsoft.com/articles/microservices-architecture-diagram/microservices-reference-arch.png)


One very successfull architecture that easily breaks down into microservices is CQRS with Domain Driven Design when coupled with an event based approach to the architecture.


![image](http://cpitman.github.io/images/queue_explosion_definition.png)
![image](http://cpitman.github.io/images/queue_explosion_solution.png)


## Advantages of microservices
- If a feature is in high demand, it's easy to instantiate more computing power focused for it. Alternatively services in low demand can require less computing power. (Better Scalability)
- Better overall control of the whole application, easier time identifying bottlenecks and points to be optimized in the system


## Disadvantages
- Can increase development time. 
- Complex behaviours require complex solutions due to the complete independency of modules locally
- Deployment and DevOps becomes significantly more complex
- https://www.forrester.com/blogs/the-death-of-microservices/


