# Structural Patterns

- Explain how to assemble objects and classes into larger structures while keeping it flexible and efficient

## Adapter

- Allows objects with incompatible interfaces to collaborate
- Problem: Stock data provider gives output in XML, but Analytics takes only JSON
- Solution: Build a converter in between that converts XML to JSON

### How it works

1. Adapter gets an interface, compatible with one of the existing objects
2. Using this interface, the existing object can safely call the adapter's methods
3. Upon receiving a acll, the adpater passes the request to the second object, but in the format that the second object expects

### Structure

1. **_Client_** is a class that contains the existing business logic of the program
2. **_Client Interface_** describes a protocol that other classes must follow to be able to collaborate with client code
3. **_Service_** is some useful class that the client cannot use directly because of incompatible interface
4. **_Adapter_** is a class that's able to work with both the client and the service. Implements the client interface, while wraping the service object
5. Client code doesn't get coupled to the concrete adapter class directly. It uses a client interface

### When to use

- When you want to use an existing class, but its interface is not compatible
- Reuse several existing subclasses that lack some common functionality that can't be added to superclass

### Pros

- Single Responsibility Principle
- Open/Closed Principle

### Cons

- Overall complexity of the code increases because you need to introduce a new set of interfaces and classes

## Bridge

- Lets you split a large class or a set of closely related classes into two separate hierarchies - abstraction and implementation - which can be devloped independently of each other
- Problem: You have shapes, but you also want to add colours, creating many subclasses
- Solution: Extend the shape class in two independent dimensions. Switch from inheritance to object composition

### Structure

1. **_Abstraction_** provides high level control logic
2. **_Implementation_** declares the interface that's common for all concrete implementations
3. **_Concrete Implementations_** contain platform specific code
4. **_Refined Abstractions_** provide variants of control logic
5. **_Client_** is only interested in working with abstraction

### When to use

- When you want to divide and organize a monolithic class that has several variants of some functionality
- Extend a class in several orthogonal/independent directions
- If you need to switch implementations during runtime

### Pros

- Create platform independent classes and apps
- Client code works with high level of abstractions
- Open/Closed Principle
- Single Responsibility Principle

### Cons

- Might make code more complex by applying the pattern to a highly cohesive class

## Composite

- Lets you compose objects into tree structures and then work with these structures as though they are individual objects
- Problem: Only makes sense when your core model can be represented as a tree
- If it is a box containing items, if it is a prodcut => return its price, if it a box => make it go over each item and find price

### Structure

1. **_Component_** interface describes operations that are common to both simple and complex elements
2. **_Leaf_** is a basic element of a tree that doesn't have sub-elements
3. **_Container_** is an element that has sub-elements => either leaves or other containers
4. **_Client_** works well with all elements through component interface

### When to use

- When you have to implement a tree like structure
- When you want the client code to treat both simple and complex elements the same

### Pros

- Can work with complex tree structures easily
- Open/Closed Principle

### Cons

- Can't provide a common interface for classes which changes too much

## Decorator

- Also known as "wrapper"
- Lets you attach new behaviours to objects by placing these inside special wrappers
- Combined effect from wearing multiple pieces of clothing

### Structure

1. **_Component_** declares common interface for both wrappers and wrapped objects
2. **_Concrete Component_** is a class of objects being wrapped
3. **_Base Decorator_** has a field for referencing a wrapped object => Should be declared as component interface
4. **_Concrete Decorators_** define extra behaviours that can be added dynamically
5. **_Client_** can wrap components in multiple layers of decorators

### When to use

- When you need to be able to assign extra behaviours to objects at runtime
- Use the pattern when it is not possible to extend an object's behaviour using inheritance

### Pros

- Extend an object's behaviour without making a new subclass
- Add or remove resposibilities from an object at runtime
- You can combine several behaviours by wrapping an object into multiple decorators
- Single Responsibility Principle

### Cons

- It is hard to remove a specific wrapper from the stack
- Hard to implement a decorator such that it doesn't depend on decorator stack
- Initial configuration code of layers might look ugly

## Facade

- Simplified interface to a library, framework or complex set of classes
- Problem: Business logic of classes would become tightly coupled to the implementation details of 3rd prty classes
- Solution: Provide a simple interface to a complex subsystem which has a lot of moving parts => Provides limited functionality
- When you call a shop to place an order, an operator is a facade

### Structure

1. **_Facade_** provides convenient access to a particular part of subsystem's functionality
2. **_Additional Facade_** class can be created to prevent polluting a single facade
3. **_Complex subsystem_** consists of dozens of various objects
4. **_Client_** uses a facade instead of calling the subsystem objects directly

### When to use

- When you have limited but straightforward interface to a complex subsystem
- When you want to structure a subsystem into layers

### Pros

- Can isolate code from complexity of subsystem

### Cons

- Can become a god object coupled to all the classes of an app

## Flyweight

- Lets you fit more objects into the available amount of RAM by sharing common parts of state between multiple objects
- Problem: A game that uses the same kind of bullets are replicated over and over, causing RAM overload and game to crash
- Solution: Let common parts of the bullets remain static, and the rest be calculated
- An object that stores only the intrinsic state is called flyweight
- Extrinsic state is moved to the container object
- Flyweight should initialize its state just once via constructor parameters

### Structure

1. It is an optimization
2. **_Flyweight_** class contains the portion of the original object's state that can be shared

- State stored in flyweight is called intrinsic and the state passed to methods is called extrinsic

3. **_Context_** of class contains extrinsic state, unique across all objects
4. **_Client_** calculates or stores extrinsic state of flyweights
5. **_Flyweight factory_** manages a pool of existing flyweights

### When to use

- Only when your program must support a huge number of objects which barely fit into RAM

### Pros

- Saving lots of RAM

### Cons

- Tradeoff between RAM and CPU cycles
- Code becomes more complicated
