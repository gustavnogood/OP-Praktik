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

## DDD
Easy: 
*Domain-Driven Design quickly
* Patterns, Principles and Practices of Domain-Driven Design by Wrox
Deeper:
*Domain-driven Design: Tackling Compleqity by Addison-Wesley
