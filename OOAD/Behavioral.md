# Behavioral Patterns

- Concerned with the algorithms and assignment of responsibilites between objects

## Chain of Responsibility

- Lets you pass requests along a chain of handlers
- Each handler decides to process or pass it on to the next one
- Problem: Want to restrict access to system so only authenticated usrs can do stuff
- Solution: Make standalone objects for each one, and if any one fails, push it out

### Structure

1. **_Handler_** declares the interface common to all concrete handlers
2. **_Base Handler_** optional class where you can put boilerplate code that's common to all handler classes
3. **_Concrete Handlers_** contain the actual code for processing requests
4. **_Client_** may compose chains just once or compose them dynamically

### When to use

- When program is expected to process different kind of requests in various ways
- Several handlers in a particular order
- Set of handlers and their order are supposed to change at runtime

### Pros

- Can control the order of request handling
- Single Responsibility Principle
- Open Close Principle

### Cons

- Some requests may be unhandled

## Command

- Turns a request into a standalone object that contains all the information about the request
- Problem: You create a neat button for text editor, but so many other subclasses extend the Button Class
- Solution: Serve as links between various GUI and business logic objects

### Structure

1. **_Sender_** is the invoker => responsible for initiating requests => triggers that command instead of sending the request directly
2. **_Command_** declares just a single method for executing the command
3. **_Concrete Commands_** pass the call to one of the business logic objects
4. **_Receiver_** contains some business logic
5. **_Client_** creates and configures concrete command objects

### When to use

- When you want to parameterize objects with operations
- When you want to queue operations, schedule their execution or execute remotely
- Implement reversible operations

### Pros

- Single Responsibility Principle
- Open Close Principle
- Undo Redo
- Assemble a set of simple commands into a complex on

### Cons

- Code may become more complicated since you are introducing a new layer between sender and receiver

## Iterator

- Traverse elements without exposing underlying implementation
- Problem: If stuff is stored in structures like trees, then how will you access if you want to access differently everytime?
- Solution: Make an iterator class that does this
- Can randomly walk around Rome, Use maps or get a tour guide => Travel Rome, with different methods though

### Structure

1. **_Iterator_** declare the operations required for traversing a collection
2. **_Concrete Iterators_** implement specific algos for traversing a collection
3. **_Collection_** interface declares one or multiple methods for getting iterators compatible
4. **_Concrete Collection_** return new instances of a particular concrete iterator each time the client requests one
5. **_Client_** works with both colections and iterators via their interfaces => Not coupled with anything

### When to use

- When collection has complex data, but you want to hide it from clients
- Reduce duplication of traversal code across app
- Code to be able to traverse different data structures or when types are unknown beforehande

### Pros

- SRP
- OCP
- Iterate in parallel
- Delay an iteration

### Cons

- Overkill if your app is simple
- Less efficient sometimes

## Interpreter

- Defines a way to interpret a domain specific language or grammar
- Define the grammar of a language and provide a way to evaluate sentences in that language
