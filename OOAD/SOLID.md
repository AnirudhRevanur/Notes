# SOLID

## Bad Design

### Rigidity

- Impact of a change is unpredictable
- Every change causes a cascade of changes in dependent modules
- Costs become unpredictable

### Fragiility

- Software tends to break in many places
- Breakage occurs in areas with no relationship
- There is a break on every fix

### Immobility

- Almost impossible to reuse any part of the software
- Useful modules have too many dependencies
- Cost of rewriting is less when compared to the risk faced to separate those parts

### Viscosity

- A hack is cheaper than the solution within the design
- Preserving design moves are difficult to think and implement

## SOLID Principles

- Robert J Martin => Principles
- Leads to flexible and stable software architecture that's less likely to break
- Michael Feathers => Acronym

### Single Responsibility Principle

- Every module or class should have only one responsibility
- Class should have only one reason to change
- Each class does only one thing
- Low Coupling of code
- Just because it can, doesn't mean it should
- Easier to test and maintain

#### Advantages

- Testing is easier
- Lower Coupling
- Organization

### Open Close Principle

- Classes, modules etc should be open for extension, but closed for modification
- Extend the existing code using features like inheritance via subclasses and interfaces
- Never modify existing interfaces
- Extend code when adding new feature

### Liskov Substitution Principle

- An object of a superclass hsould be replaceable by objects of its subclasses without causing any issues
- Child class should never change the characteristics of its parent class

### Interface Segregation Principle

- Clients should not be forced to use interfaces that they do not use/need

### Dependency Inversion Principle

- High Level modules should not depend on low level modules, both should depend on abstractions
- Details should depend on abstractions
- Decouple high-level and low-level classes
