# GRASP

- General Responsibility Assignment Software Patterns
- Craig Larman in 1977
- 9 fundamental principles in object design

## Responsibility

- A contract/obligation that a class/module/component must accomplish
- Responsibility can be accomplished by single object or a group of objects
- Translation of responsibilities into classes and methods is influenced by granularity of responsibility

### Doing

- Doing something itself like creating an object of doing a calculation
- Initiating action in other objects
- Controlling and coordinating activities in other objects

### Knowing

- Knowing about private encapsulated data
- Knowing about related objects
- Knowing about things it can derive or calculate

## Design Principles

- Creator
- Information Expert
- Low Coupling
- High Cohesion
- Controller
- Polymorphism
- Indirection
- Protected Variation
- Pure Fabrication

### Creator

- Decides who creates an object or creates an instance of some class based on interaction and association of the object

### Information Expert

- Objects do things related to the information they have
- Info necessary may be spread across several classes => Objects interact via messages
- Just because an object has information necessary doesn't mean it will have responsibility for action related to the information
- Have all the info needed to perform operations or collaborate with others to fulfill their responsibilities

### Low Coupling

- A measure of how strongly one element is linked to or relies on other elements
- Minimizes the dependency, hence making the system maintainable, efficient and code reusable
- High Coupling leads to issues as it becomes harder to reuse
- Assign responsibilities so that coupling remains low
- Two elements are coupled if one element implements or extends the other element

### Controller

- Deals with how to delegate the request from the UI layer to domain layer
- Minimizes dependency between GUI components and system operation classes
- Can reuse the controller class
- Delegates work to other objects instead of doing work itself

### High Cohesion

- A measure of how strongly related and focused the responsibilities of an element
- Low coupling => Does too many unrelated tasks => Hard to understand and reuse

### Polymorphism

- Deals with how to act different depending on object's class
- Handle related but varying elements based on type
  - Adhoc => overloading
  - Parametric => Early binding
  - Inclusion => Sub typing
  - Coercion => Casting

### Indirection

- Assign responsibility to intermediate class for providing linking between objects that are not linking directly

### Pure Fabrication

- Assign a highly cohesive set of responsibilities to an artificial or convenience class that dodes not represent a domain concept

### Protected Variation

- Instability should not have an impact on other elements
- Open/Close Principle
- Variation and Evolution Points
