# Secure-by-Design
notes from the book Secure by Design 

## Chapter 1
summary:
* It's better to view security as a concerne to be met than to view it as a set of features to implement.
* It's impractical to achive sequrity by keeping it at the top of your mind all the time while developing. A better way is to find design practices that guide you to more secure solutions.
* Any activity involving active decision-making should be considerd part of the software design process and can thus be referred to as design.
* Design is the guiding principle for how a system is built and is applicable on all levels, from code to architecture.
* The traditional approach to software security struggles because it relies on the developer to explicity think about security vulnerabilities while at the same time trying to focus on implementing business functionality. It requires every developer to be a security expert and assumes that the person writing the code can think of every potential vulnerabilty that can occur now or in the future.
* By shifting the focus to design, you're able to achive a high degree of software security without the need to constantly and explicitly think about security.
* A strong design focus lets you create code that's more secure compared to the traditional approach to software security.
* Every XML parser is implicity vulnerable to entity attacks because entities are part of the XML language
* Using generic types to represent specific data is a potential door opener for security weaknesses.
* Choosing the XML parser configuration is difficult without understanding the underlying parser implementation.
* Secure by design promotes security in-depth by adding several layers of security.

## Chapter 2
Summary:
* incomplete, missing or shallow modelling leads to a design with security flaws.
* A security flaw in the form of broken buisness integrity can live in production for a long time, bleeding money from your enterprise.
* Consius, explicit design results in a much more robust solution

## Chapter 3 
Summary:
* Building domain models is a good way to promote deep learning about the domain.
* A domain model should be strict and unambigous representation of the domain that captures only the most important aspects.
* When creating a domain model, you make a choice among many possible models.
* The domain model forms a language fo communictaing about the system.
* Entities, value objects and aggregates are the basic build blocks for your domain model.
* Entities hav an identity that's consistent during their life cycle and contain other entities or value objects.
* The uniqueness of entities always has a scope, and that scope depends on your model.
* A value object doesn't have an identity but rather is defined by its value.
* A value object must always be immutable and should form a conceptiual whole.
* An aggregate is a conceptual boundary that groups together other model objects and is reponsible for upholding invariants among those objects.
* An aggregate always has an  aggregate root and, in code, that root is typaclly the same as the aggregate.
* The aggregate root has global identity bacause this is the only part of the aggregate that parts of the model can hold a reference to.
* The ubiquitous language is spoken by everyone on the team, including domain experts, to ensure a common understanding.
* The domin model is bound by the semantics of the ubiquitous language.
* The bounded context is the context in witch the semanics of the model hold. As soon as the semantics change, the model breaks and the boundry of the context is found.
* Using Conway's Law is a good starting point when trying to find the boundry of a context.
* Data crossing a semantic boundry is of special intrest from a security perspective bacuase this is where the meaning of a concept could implicitly change.

## Chapter 4
Summary:
* Data integrity is about ensuring the consitency and accuracy of data during its entire life cycle.
* Data availability is about ensuring data is obtainable and accesible at the expected level of performance in a system.
* Immutable values are safe to share between threads without locks: no locking, no blocking
* Immutability solves data availability issues by allowing scalability and no locking between threads.
* Immutability solves data integrity issues by preventing change.
* Contracts are an effective way to clarify the responsibilities of objects and methods.
* It's better to fail fast in a controlled manner than to risk uncontrolled failures later. Fail fast by checking preconditions early in each method.
* Validation can be broken down into checking origin, data size, lexical content, syntactic format, and semantics.
* Origin checks can be done by checking the origin IP or requiring an acces key to counteract DDoS attacks.
* Data size checks can be done both at the system border and at object creation.
* Lexical content checks can be done with a simple regular expression (regexp).
* Syntax format checks might require a parser, wich is more expensive in terms of CPU and memory.
* Semantics checks often require looking at the data in the database, such as searching for an entity with a speciic ID.
* Earlier steps in the validation order are more economical to performe and protect the later, more expensive steps. If early checks fail, later steps can be skipped.

## Chapter 5
Summary:
* Domain primitives are the smallest building blocks and form the basis of your domain model.
* You should never represent a concept in your domain model as a language primitive or a generic type.
* If a term in your domain already exists outside of your daomin but with a slightly different meaning, you should introduce a new term instead of redifining the existing one.
* A domain primitive is immutable and can only exist if it's valid in the current daomin.
* You should harden API's by using your domain primitive library.
* a read-once object is a useful way to represent sensitive data in your code.
* The value of a read-once can only be retrived once.
* The read-once object design pattern can mitigate leakage of sensitive data.
* Domain primitives provide the same type of security that concurrent taint analysis would.

## Chapter 6
Summary:
* Entities are the preffered way to handle mutable states.
* Entities must consist on creation.
* No-arg constructors are dangerous.
* The builder pattern can be used to construct entities with complex constraints.
* You need to protect the integrity of attributes when they'r accessed.
* A private data field with unrestricted getter and setter methods isn't more secure than a public data field.
* You should avoid sharing mutable objects and use immutable domain primitives instead.
* You shouldn't expose a collection, but rather expose a useful property of the collection.
* Collections can be protected by exposing an unmodifiable version.
* You must take care so that the data in a collection can't be changed from the outside.

## Chapter 7
Summary:
* Entities can be designed to be partially immutable.
* State handling is easier to test and develop when extracted to a seperate object.
* Multithreaded environments for high capacity require a careful design.
* Database locking can put a limit on availability of entities.
* Entity snapshots are a way to regain high availability in multithreaded enviroments.
* Entity relay ( when fulfillment of one entity gives rise to another) is an alternative way to model an entity that has a lots of different states.

## Chapter 8
Summary:
* By dividing test into normal testing, boundry testing, invalid input testing, and extreme input testing, you can include security in your unit test suits.
* Regular expression can be sensitive to inefficient backtracking, and, therefore, you should check the length of input before sending it to the regular expression engine.
* Feature toggles can cause security vulnerabilities, but you can mitigate those vulnerabilities by verifying the toggle mechanism using automated tests.
* A good rule of thumb is to create a test for every toggle you add, and you should test as small as possible.
* The toggle mechanism itself can be subjected to auditing and record keeping.
* Incorporating automated security tests into your build pipeline can give you the ability to run a mini penetration test as often as you like.
* Availability is an important security aspect that needs to be considered in every system.
* Simulation DDoS attacks helps in understaing weakneses in the overall design.
* A domain DoS attack is extremly difficult to protect against because it's only the intent that distinguishes it from regular usage.
* Many security problems are caused by misconfiguration, and the cause for faulty configuration can be either unintentional changes, intentional changes, or missunderstood configuration.
* Configuration hot spots are good indicators for finding areas in your configuration where testing is most critical.
* It's important to know the default behavior of the tools you use and assert that behavior with tests.

## Chapter 9
Summary:
* Separating buisness exceptions and technical exceptions is a good deisgn strategy because technical details don't belong in the domain.
* You shouldn't intermix technical and business exeptions using the same type.
* it's good design practice to never include business data in technical exceptions, regardless of wether it's sensitive or not.
* You can create more secure code by designing for failures and treating failures as normal, unexceptional reults.
* Avilabilty is an important security goal for software systems.
* Resiliance and responsivness are traits that add security by improving the availability of a system.
* You can use design patterns lika circuit breakers, bulkheads, and timeouts to design for avilability.
* Repairing data before vaildation is dangerous and should be avoided at all cost.
* You should nere echo input verbatim.

## Chapter 10
Summary:
* The twelve-factor app and cloud-native concepts can be used to increase the security of applications and systems
* You should run your application as a steless processes that can be started or decomissioned for any occasion.
* Any result of processing should be stored to a backing service, such as a database, log service or distributed cache.
* Separating code and configuration is the key to allowing deployment to multiple enviroments without rebuildning the application.
* Sensetive data should never be stored in resource files, because it can be accessed even after the application has terminated.
* Configuration that changes with the enviroment should be part of the enviroment.
* Administration task are important and should part of the solution; they should be run as processes on the node.
* logging shouldn't be done to a local file on disk, because it yealds several security issues.
* Using  a centralized logging service yeilds several security benefits, regardless of wether you're running an application in the cloud or on-premise.
* Service discovery can increase security by improving availability and promoting an ever.changing system.
* Applying the concept of the three R's - Rotate, Repave and repair. Significantly improves many aspect of security. Designing your applications for the cloud is a prerequisit for doing this.

## Chapter 11
Summary:
* Do deliberate discovery early to get deep insights into subtle aspects of the domain.
* Start Specific, then abstract later.
* Collect expertise from all adjacent domains.
* Refactor names if they change semantics, especially if they change semantics outside hte bounded context

## Chapter 12
Summary:
* Introducing domain primitives should be done at the semantic boundry of your context.
* Ambigous parameters in APIs are common source of security bugs.
* You should be on the lookout for ambigous parameters when reading code and adress them using the direct approach, the discovery approach, or the new API approach.
* Never log unchecked user input, because it opens up the risk of second-order injection attacks.
* Limit the number of times a sensitive value can be accessed, because it allows you to detect unintentional access.
* Use explicit accessor methods for data that you want to log. Otherwise, new fields can end up in logs by accident.
* Because defensive code constructs can be harmful, clarify them using contracts and domain primitives.
* The DRY (dont repeat yourself) principle is about repeated representation of knowledge, not about repeated text.
* Trying to reduce repeated tet that isn't repeated knowledge can cause unnecessary dependencies.
* Failing to reduce repeated knowledge because the textdiffers can cuase vulnerable inconsistencies.
* Test reveal possible weaknesss in your code, and you should look for invalid and extreme input tests.
* Ensure that your domain primitives encompass an entire conceptual whole.
* Be on the lookout for domain types lacking proper validation and adress them with domain primitives and secure entitites.


# Domain Driven Design DDD

## Best practise - An introduction to DDD
[Från microsoft](https://learn.microsoft.com/en-us/archive/msdn-magazine/2009/february/best-practice-an-introduction-to-domain-driven-design)

### The Platonic Model
### Talk the Talk
### Context
### Know Your Value Proposition
### A System of Single Responsibilities
### Entities Have an Identity and a Life
### Value Objects Describe Things
### Aggregate Roots Combine Entities
### Domain Services Model Primary Operations
### Repositories Save and Dispense Aggregate Roots
### The Thing with Databases
### Getting Started with DDD

## Solid
SOLID is an acronym for five design principles — Single Responsibility Principle (SRP), Open-Closed Principle (OCP), Liskov Substitution Principle (LSP), Interface Segregation Principle (ISP), and Dependency Inversion Principle (DIP).
These principles guide developers to create maintainable, flexible, and robust software systems. In this article, we will explore each of these principles in-depth, accompanied by practical code examples in C#.
[Artikeln för mer läsning och kodexempel](https://medium.com/@edin.sahbaz/comprehensive-guide-to-solid-principles-in-c-54d79e19b7d7)

### Single responsebility (SRP)
The SRP states that a class should have only one reason to change, meaning it should have a single responsibility. This principle helps in maintaining code that is easier to understand, test, and maintain.

### Open-Closed Principle (OCP)
The OCP states that software entities (classes, modules, etc.) should be open for extension but closed for modification. It encourages the use of abstraction and inheritance to achieve this principle.

### Liskov Substitution Principle (LSP)
The LSP states that objects of a superclass should be replaceable with objects of its subclasses without affecting the correctness of the program. In simpler terms, it ensures that derived classes can be used interchangeably with their base classes.

### Interface Segregation Principle (ISP)
The ISP states that clients should not be forced to depend on interfaces they do not use. It promotes the idea of segregating large interfaces into smaller and more specific ones.

### Dependency Inversion Principle (DIP)
The DIP states that high-level modules should not depend on low-level modules; both should depend on abstractions. It encourages loose coupling between modules and facilitates easier unit testing and maintainability.

### Conclusion
The SOLID principles provide valuable guidelines for designing maintainable and extensible software systems. By applying these principles, developers can create code that is easier to understand, test, and maintain.

# Books to read
## Architecture
Clean architecture by Robert c Martin

## DDD
### Easy: 
* Domain-Driven Design quickly
* Patterns, Principles and Practices of Domain-Driven Design by Wrox

### Deeper:
* Domain-driven Design: Tackling Compleqity by Addison-Wesley

# Skills to develop
* Microtjänster
* Hur man strukturerar ett projekt/microtjänst/Web-API


