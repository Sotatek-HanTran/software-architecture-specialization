# software-architecture-specialization

## Software architect
- Architecture documentation is about understanding the value of a decision we're gonna make;
- What value I am adding as a software architect?
- Requirements are not our primary driver. Requirements are a fundamental part of a project which is a temporarily limited activity to deliver a set of functions to an organization.
    - Those functions have:
        - Profitability
        - Constituent Value
        - Reuse
        - Grow market size
        - Grow market quality
- The architect asks WHY?
- How does a software developer architecture document is different from a software architect's?
    - Their designs are fundamentally different jobs;
        - The developer's job is to implement it as good as possible according to the project requirements. Because if he asks all the WHYs about everything, we never get any code ready. He's job is to deliver on time and on budget;

## An archutecture must
- Describe why technology decisions were made
    - Connects requirement to design choices
- Describe HOW it is used
    - Description of technology usage
    - Include coding patterns and/or prototype information
- Describe the governance and usage
    - EA integration
    - Governance information
    - Architecture analysis

## Issues due to lack of architecture
- Big ball of mud
- Spaghetti code
- Inconsistent approaches to solving same problems
- Quality attributes ignored
- Deployment problems
- Maintenance issues

## Important questions
### General questions
- How do I design effectively and minimally?

### Business related questions
- Is the ROI real?
- Are the components strategic?
- Can they be used to make money?
- How does this impact the overall deployment topology?
- What else is being built?
- Can the organization handle it?
- Will the organization accept it?
- Is it just reliable enough? Secure enough? usable enough?

### Technical questions
- Does the picture reflect what we want to build?
- Is it going to work?
- Have you identified and mitigated the highest priority risks?

---

## Definitions
- Software design: Looks at the lower-level aspects of a system;
- Software architecture: Looks at the higher-level aspects of a system;
- Functional requirements: What the system is expected to do;
- Non-Functional requirements: How well the system does what it does.
- Programming paradigm: The way a program is written;
    - Imperative paradigm: Breaks large operations into smaller programs called subroutines (like methods)




## Principles
- Simplicity first! Make knowledge transfering low;

## Observations
- Try playing with people much better than you;
- Architecture represents significant decisions, where significance is measured by cost of change;
    - Significant decisions:
        - Architecture (Programming language, architecture style)
        - Design
        - Implementation (Indenting tabs)
- Base your architecture on requirements, travel light and prove your architecture with concrete experiments (Poc, prototype, spike, tracer, vertical slice, walking skeleton, executable reference architecture, etc);
- Components responsabilities are often described as verbs. E.g., search;
- As an architect stablish what quality attributes are negotiable and the ones that must be done;
- We can invest in anything as long as we measure the value we received in some fashion;

## Content

## Object-Oriented Analysis and Design
### Eliciting Requirements (Design Process)
The phase to clarify requirements that the client did not tell.

This activity involves producing a *Conceptual Design* and a *Technical Design*, that results in two artifacts: *Conceptual Mockups* and *Technical Diagrams*;

During the conceptual design we talk about:
- Mockups
- Requirements
- Tradeoffs

Conceptual Mockups provide initial thoughts on how the requirements will be satisfied;

- Identify major components and connections;
    - Each component has a task it needs to perform. It is a responsability;
- Work on the Technical Design, that describes how these responsabilities are met; This is done by splitting the components into smaller components;

### Object-oriented thinking
User story: As an online shopper, I want to add an item to my shopping cart, so that I can purchase it.

Objects:
- User;
- Item;
- Shopping cart;

Behaviours:
- Add;
- Purchase;

Connections:
- User and shopping cart;
- User and items;
- Shopping cart and items;


#### Object categories
- Entity Objects: Real world entity;
- Boundary Objects: Sit at the boundary between systems;
- Control Objects: Responsible for coordination;

#### Quality attributes
##### Competing qualities (Quality vs Time to market)
- Usability
- Scalability
- Performance
- Convenience
- Security
- Reusability
- Flexibility
- Maintainability

Always validate the project quality

Tradeoffs
- Performance vs Security
- Performance vs Maintenability
- Performance vs Backwards compatibility

Context is important what choice of solution is right for the quality of the balance;

#### Class Responsability Collaborator (CRC)
To represent components, connections and responsabilities in the *Conceptual Design* phase we use CRC cards;

Good for prototyping and simulating high level design;

CRC cards are used to Identify, Organize and Refine the components in the conceptual design;

CRC Structure:
- Class name (Component name);
- Responsabilities;
- Collaborators: Other classes the class interacts with (connects to) to fulfill its responsabilities;

### Creating models in design
#### Design principles
Design principles lead to software that is Flexible, Reusable and Maintainable;

The goal of Object-oriented design is to:
- Make an abstract data type easier to write;
- Structure a system around abstract data types called classes;
- Introduce the ability for an abstract data type to extend another by inheritance;

#### Four design principles
- Abstraction: Simplifying a concept to its essentials within some context. Ignoring unimporrtant details;
    - They have definitions of what attributes or responsabilities the subject should have. Not implementations;
- Encapsulation: Self-contained object with data and functions it requires to work. Exposes an interface that other objects can access and use it, and restricts access to certain inside details;
    - Black box thinking (Abstraction barrier): The other classes do not need to know how certain method is implemented. Just its result;
- Decomposition: Taking a whole thing and dividing it into parts. On the flip side, taking a bunch of separate parts with different functinalities and combining them to form a whole;
    - It is important to understand how the parts relate to the whole, considering:
        - Fixed or dynamic number;
        - Lifetime: Does it exists independently?
        - Sharing: Does the part performs different roles in different wholes? Do we want it to be possible?
    - Types of decomposition (They define the interaction between the whole and the parts)`:
        - Association: Interaction between two independent objects;
            - UML connection: Straight line;
            - Example: Car - passengers
        - Aggregation: "Has-a" relationship. The whole has a part that belongs to it. These parts can be shared among other wholes. The relationship is weak since the parts can exist independently;
            - UML connection: Empty diamond in the whole side;
            - Example: Bookshelf - books
        - Composition: Exclusive containment of parts. A strong Has-a relationship. The whole cannot exist without parts. If it loses any of its parts the whole ceases to exist. If the whole is destroyed then all of its parts are destroyed too.
            - Usually we can only access parts through its whole;
            - The parts are exclusive to the whole;
            - UML connection: Fulfilled diamond in the whole side;
            - Example: House - Room
- Generalization: Factorying repeated, common and shared characteristics into one class;
    - Allows us to apply DRY;
    - Achieved by inheritance;
    - Helps to reduce the amount of redundancy when resolving problems;

### Expressing design structure with UML
#### Generalization with Inheritance

- Represented by a solid line
- Superclass (Generalized classes) at the head of the arrow
- Subclass (Specialized classes) at the tail

Protected attributes can only be accessed by:
- Encapsulating class itself;
- All subclasses;
- All classes within the same package (namespace that represents those classes);

Explicit constructors allows us to assign values to attributes during instantiation;

#### Generalization with Interfaces
- An interface is a contract to be fulfilled by implementing classes;
- Interfaces are not generalization of classes. Just used to describe behaviours, not attributes;
- The UML notation for interface implementation by a class is a dotted arrow.
    - Interface touches the head of the arrow;
    - Class touches the tail of the arrow;


#### Classes relationships
- Dependency: Class A uses class B. But class A does not contain an instance of B as part of its own state.
    - UML notation: dashed open arrow
- Association: A stronger dependency relationship. It is a one-way relationship. Class A contains an instance of B. But B does not know about A.
    - UML notation: solid open arrow
- Generalization: Inheritance
    - UML notation: solid closed arrow
- Realization: Interface (contract) implementation
    - UML notation: dashed closed arrow

---
## Sequence Diagrams
Show how the objects interact with each other to complete tasks;
### Components
- Actor
- Objects (:Name of the class)
- Lifelines (dashed vertical lines)
- Messages (solid arrows)
    - Response (dashed arrow)

### Alternative process
- When this alternative will occur
    - Example: [ Tv viewer knows what channel they want ]
- [ else ] process
- loop
    - Example: [ Tv viewer does not like the channel ]

## Design Principles
### General guidelines to evaluate the structure of your software solution
- Flexibility
- Reusability
- Maintainability

#### Evaluating design complexity
Well designed systems are like lego blocks where we can connect two blocks without much trouble.

Bad designed systems are like puzzles where we can only connect pieces to other specifics puzzle pieces and nothing else.

- Module: Class and methods inside it
- Metrics for evaluating complexity:
    - Coupling: Complexity between the module and other modules;
        - When evaluating the coupling of a module we consider:
            - Degree: Number of connections between the modules and others;
                - Keep it small. Connection through few parameters or narrow interfaces;
            - Ease: How obvious are the connections between the module and others. We want the connections to be easy to make without needing to understand the implementations of the other modules;
            - Flexibility: How interchangeable the other modules are for this module. We want to be able to replace the module for something else better in the future;
    - Cohesion: Complexity within a module. It represents the clarity of responsabilities within a module;
        - High cohesion: One clear purpose;
        - Low cohesion: If the module encapsulates more than one purpose or has an unclear purpose;

#### Principles to achieve Flexibility, Reusability and Maintainability
- Design principles questions:
    - What attributes and behaviours do we need to model a class through abstraction?
    - How are these attributes and behaviours grouped together and accessed through encapsulation?
    - Can my class be simplified into smaller parts using decomposition?
    - Are there common things among my objects that can be generalized?
- Separation of concerns
    - Some concerns can lead to more concerns so we have to consider:
        - What information the implementation represents;
        - What it manipulates;
        - What gets presented at the end;

#### Information Hiding
- need-to-know;
- Modules only have to have access to the information needed to perform their task;
- Parts that might change should be hidden. E.g., Implementation details;
- Parts that should not change are revealed through interfaces;

#### Conceptual Integrity
- It is about designing and implementing a software in a consistent manner. As if it was written by one person;
- To achieve this we should have a well defined design and architecture;
- Decisions on how the system will be designed and implemented;

### Generalization Principles
Use when subclasses provide and share attributes and behaviors from the same superclass, but each subclass has their own distinct functions.

How to know if we are abusing inheritance? Ask:
- Am I using inheritance to simply share attributes or behavior without further adding anything special in my subclasses? Yes = Abusing
- Am I breaking Liskov Substitution Principle? Yes = Abusing
    - It states that a subclass can replace a superclass, if and only if, the subclass does not change the functionallity of a superclass;

### Modeling Behaviour
#### UML Sequence diagram
Describes how objects in a system interact to complite a specific task.

Should be represented from left to right in the order they interact with each other.

Components:
- Actor (starts the entire process)
- Labeled box
- Lifeline
- Messages (solid line from sender to receiver)
    - Response (return of control) (dashed line)
- Activation

#### UML State diagram

It describes how the system, components or objects behave and respond when events occur.

- State: A way an object exists at a particular point in time. The state of an object is determined by the values of its attributes;
    - It has three sections:
        - State name (Required)
            - E.g., Full
        - State variables: Data relevant to the state of the object;
            - E.g., Students (in a course context)
        - Activities
            - Actions that are performed when in a certain state;
                - Types of activities:
                    - Entry: When entered from another state;
                    - Do: Occur once or multiple times while in a certain state;
                    - Exit: When state is exited and moves on to another state;
- Transition: Events that change states
    - UML Notation: Solid line fulfilled arrow from one state to another;
    - Each transition will always have an event and may have a guard condition, and an action;
    - E.g.: 
        - Event: Click submit button.
        - Guard condition: Submit date before due date. 
        - Action: Submit test
- Termination: An object being destroyed or the process being completed;
    - UML notation: Circle with a filled circle inside;

### Model Checking

This should be done after coding and before deploying;

It is a technique that does state exploration;
E.g.: Given that you started in this current state, explore all the ways you can go into the future and reason about what all those future states can look like.

Model checkers generate a state model from code;
State model: Abstract state machine that can be in one of various states. The model checker then checks that state model conforms to certain behavioral properties; 

Phases to perform model checking:
- Modeling phase: Here we enter the model description and desired properties.
    - Here we can verify sanity checks
    - E.g., Turning on and off a light bulb switcher
- Running phase: Run the model checker to see if our model conforms with the desired properties wrote in the modeling phase;
- Analysis phase: Check if all the properties were satisfied or violated (counterexamples)

Semantics

How do we improve our ability to reason about software using states?

---

## Design patterns

It is a pratical proven solution to a recurring design problem;

### Gang of four

There are 23 patterns in this catalog

#### Categories
##### Creational Patterns (How we create new objects)

We can create or clone objects;

- Singleton Pattern
    - Design goal: Only one object of a class that is globally accessible;
    - Example: App settings, print queue, software driver for a device;
    - Implementation prerequisites:
        - Private constructor
        - Private class variable that references the one object of the class;
        - Public static method to get the class variable. Instantiate if not exist;
    - Lazy creation: Does not create an object until it is truly needed;
    - If there are multiple threads running, there could be issues caused by the threads trying to access the shared single object;

- Factory Method Pattern
    - Design goal: Defines an interface for creating objects, but let the subclasses decide which class to instantiate;
    - Factories allow client code to operate on generalizations; I.e., Coding to an interface, not an implementation;
    - Concrete instantiation: Instantiate a class based on a provided type;
        - E.g., new Product product;
    - Factory Object: Object that creates other objects; Could be useful if many parts of the software want to create the same objects;
    - Factory Method (Abstract class): Object creation is made by other method. Now instead of using the factory object, we specialize into the class that will use the factory method;

##### Structural Patterns (How objects are connected to each other)
- Also specify how subclasses and classes interact through inheritance;
- Facade Pattern
    - Design Goal: Provides a single simplified interface for client classes to interact with the system;
        - It is a wrapper class that encapsulates a subsystem in order to hide its complexity (by information hiding design principle);
    - Does NOT add functionallity;
    - Acts as an point of entry into the subsystem;
    - A Facade class can be used to wrap all the interfaces and classes for a subsystem. So it is our decision to decide what we want to wrap;
    - Steps:
        - Design the interface that will be implemented by the different classes;
        - Implement the interface with one or more classes;
        - Create the Facade class and wrap the classes that implement the interface;
        - Use the Facade class to access the subsystem;
    - While the facade design pattern uses a number of different design principles, its purpose is to provide ease of access to a complex subsystem. This is done by encapsulating the subsystem classes into a Facade class, and then hiding them from the client classes so that the clients do not know about the details of the subsystem. 
- Adapter Pattern
    - Design Goal: Solve situations where the output of one system may not conform to the expected input of another system;
    - The adaptee is hidden from the client by the wrapping adapter class;
    - An adapter is meant to:

        - An adapter is meant to wrap the adaptee and expose a target interface to the client;
        - Indirectly change the adaptee's interface into one that the client is expecting by implementing a target interface;
        - Indirectly translate the client's request into one the ad`aptee is expecting;
        - Reuse an existing adaptee with an incompatible interface;
    - Steps:
        - Design the target interface;
        - Implement the target interface with the adapter class;
        - Send the request from the client to the adapter using the target interface;
- Composite Pattern
    - Design Goal: Compose nested structures of objects and deal with the classes for these objects uniformly;
    - Solves:
        - How do we use individual types of objects to build a tree-like structure?
        - How do we treat individual objects uniformly without checking their types?
            - This is achieved by:
                - Enforcing polymorphism across each class implementing an interface (or inheriting from a superclass)
                - Using a technique called `Recursive Composition`, which allows objects to be composed of other objects that are of a common type;
    - Steps:
        - Design the interface that defines the overall type;
        - Implement the composite class;
        - Implement the leaf class (Does not contain any components within);

- Proxy Pattern
    - Design Goal: A Proxy class represents a real subject class;
        - Scenarios to use proxy pattern:
            - Act as a virtual proxy: For heavy tasks. We use a lightweight proxy in place of a resource intensive object until it is actually needed;
            - Act as a protection proxy: Check permissions;
            - Act as a remote proxy: The proxy class is local and the real subject is remote;
                - Implementation of a verification of requests from client in order to determine if, how, and to whom the requests should be forwarded to;
    - Steps:
        - Design the subject interface (this will be implemented by the proxy and the real subject;
        - Implement the interface in the real subject class;
        - Implement the proxy class;

- Decorator Pattern
    - Design Goal: Allows objects to dynamically add behaviors to others and reduce the number of classes needed to offer a combination of behaviors.
    - Aggregate other types of components, which will allow us to "stack" components on top of each other;
    - Makes use of interfaces and inheritance;
    - Steps:
        - Design the component interface (defines the common behavior the concrete component and concrete decorators will have;
        - Implement the interface with the base concrete component class;
            - This should be the FIRST ONE in the stack;
        - Implement the interface with the abstract decorator class;
            - It contains only ONE instance (aggregation) of the interface implementation class;
        - Inherit from the abstract decorator and implement the component interface with concrete decorator classes;


##### Behavioral Patterns (How objects collaborate to achieve a common goal)
- How each object does a single cohesive function, and also how independent objects work towards a common goal;

- Template Method Pattern
    - Design Goal: Define the skeleton of an algorithm in an operation, letting the subclasses redefine certain steps without changint the algorithm's structure;
    - Useful when we have two classes with same functionality, in the same sequence, but different implementations;

- Chain of responsibility Pattern
    - Design Goal: Pass requests to the next handler so one of them can successfully handle it; If no handler can resolve the request then it will no be satisfied;
    - Steps in the concrete handler:
        - Check if the rule matches
        - If it matches, do something specific;
        - If doesn't match, call the next filter in the list;
    - It can be combined with the `Template Pattern` so we can ensure each handler will handle the request in a similar way, following the required steps;

- State Pattern
    - Design Goals: Change an objects behavior based on its state at runtime;
    - Elements involved:
        - Context: Keeps track of the current state;
        - State
            - ConcreteStateA
            - ConcreteStateB

- Command Pattern
    - Design Goals: Encapsulate a request as an object of its own
        - The Command pattern creates a command object between the sender and receiver. The command object then calls the method in the receiver;
        - The receiver does not have to know about the receiver or what methods to call;
    - We use this pattern for the following situations:
        - Store and schedule different requests;
        - Store commands into lists;
        - Manipulate the commands before they are completed;
        - Put the commands onto a queue;
        - Implement undo/redo functionality;
        - Store commands in a log list so they can be reexecuted in case the program crashes;
    - Steps:
        - Create the interface which will be implemented by the receiver;
            - Add all the different methods the concreteCommands will have;
        - Create the receiver;
        - Create the command interface that will have to be implemented by all commands;
        - Create tha classes that represent the commands and implement the command interface;

- Observer Pattern
    - Design Goals: Notify subscribers of changes in the observed subject;
    - Steps:
        - Create a superclass that has three methods:
            - Subscribe;
            - Unsubscribe;
            - NotifyAll;
        - Create an Observer interface so the observers can update themselves;


## MVC
### Antipatterns (code smells)

They are the bad design;

The mvc uses the Separation of Concerns design principle to divide the main responsabilities in an interactive system;

- Model (like the back end)
    - Entity object;
    - Updates the view by using the Observer Design Pattern;
    - Contains the underlying data and logic that users want to see and manipulate;
    - Self contained: Has all the states, methods and other data that it needs to exist on its own;
    - Should notify the observers whenever there is a change;
- View (like the front end)
    - Boundary object;
    - Presents the model information to the user in a way they expect it and allows them to interact with it;
    - Uses the controller;
    - Gives the user a way to see the model, or at least part of it;
    - The view does not send requests directly to the model. Instead it sends messages to the controller;
- Controller
    - Control object that receives events and coordinates actions;
    - Modifies the model;

### Design principles underlying design patterns

#### Liskov substitution principle
A subclass should be able to substitute its baseclass since no behaviour from the base class should be changed;

Ps: We can change how the subclass achieve certain goal however we should keep the input and output the same;

If we're writing objects which extend classes but fails the `Is-A` test, we're likely violating this principle.

#### Open/Closed principle
A class should be open for extension (through inheritance or interfaces) but closed for changes;

- It helps to keep a system stable by closing classes to changes
    - If we to not want a class to be extended we can set it as `final`;
- We can consider a class `closed` when:
    - It is tested;
    - All attributes and behaviors are encapsulated;
    - Proven to be stable;

#### Dependency inversion principle
States that high level modules should depend on high level generalizations, and not on low level details;

E.g., clients should depend on abstract classes or interfaces instead of referencing concrete resources; And the concrete resources (`low level`) should have their behavior generalized into an interface (`high level resource`) or abstract class(`high level resource`); This way the clients can be independent from low level functionality;

- High level resources (Define a general set of behaviors):
    - Abstract class;
    - Interface;
- Low level resources (Provide implementation for behaviors):
    - Concrete classes;

- High level dependency: When clients have reference to abstraction classes or interfaces;
- Low level dependency: When clients have reference to concrete classes;

#### Composing objects principle
States that classes should achieve code reuse through aggregation rather than inheritance;

- Advantages:
    - More flexibility;
    - During the design phase it is easier to keep classes separated; Composing objects do not force us to try to find commonalities between classes and couple them together like with inheritance. Instead we can design classes that work together without having to share anything between them; It also helps when requirements change. If we use inheritance we'd have to restructure the inheritance tree;
    - Aggregation and delegation offers less coupling than inheritance since the composed classes don't share attributes or implementations of behaviors;
    - Allows us to dinamically change the behaviors of objects at runtime;
- Disadvantages:
    - You should provide implementation for all behavior without the benefit of inheritance to share code. This means that we may have similar implementations across classes;

- Important questions to decide between inheritance or composition:
    - Do you have a set of related or unrelated classes?
    - What is a common behavior between them?
    - Do you need specialized classes to handle specific cases or do you simply need a different implementation of the same behavior?

#### Interface segregation principle
States that a class should not be forced to depend on methods it does not use. This means that any classes that implement an interface, should not have "dummy" implementations of any methods defined in the interface. Instead, you should split large interfaces into smaller generalizations.

Interfaces are descriptions of what parts of your system can do;

#### Principle of least knowledge (Law of Demeter)
Important: Sometimes we cannot avoid violating this principle. And we should decide how much coupling is tolerable;

A class should be designed so that it does not need to know about and depend upon almost every other class in the system;

They should interact with as few other classes as possible. Only with its immediate `friends`;

- Rules:
    - First: A method `M` in an object `O` can call on any other method within `O` itself;
        - A method encapsulated within a class is allowed to call any other method that is also encapsulated within the class;
    - Second: A method `M` can call the methods of any parameter `P`;
        - The parameter is `local` to a method so it is considered a `friend`;
    - Third: A method `M` can call a method `N` of an object `O` if `O` is instantiated within `M`;
        - The same as the second;
    - Fourth: A method `M` in object `O` can invoke methods of any type of object that is a direct component of `O`;
        - Instantiated within `O`;

You should not access methods `reaching throught` other objects; E.g., you should not invoke any methods of objects that are not local.

- Reach through means we need another object to pass along our request or we are using methods from objects that are considered outside of our immediate friends;
    - These situations occur when we have a chain of method calls to objects we should not know about. 
        - E.g., `this.car.engine.start()`;
    - Or when we use methods from an unknown type of object that is returned from a local method call. Returned objects should be the same type as:
        - Those declared in the method parameter;
        - Those delcared and instantiated locally in the method;
        - Those delcared in instance variables of the class that encapsulates the method;

Local objects means that they should be passed in through a `parameter` or `instantiated within a method`, or `instance variables`.

#### Code smells (16)

Refactoring: Process of making changes to the code so that external behaviors are not changed, but the internal structure is improved;

Book: `Refactoring: Improving the design of existing code - Martin Fowler`

- Code smells (07):
    - Comments:
        - Useful for documenting APIs;
        - Documenting decisions;
        - Sometimes comments can be an indicator of bad design;
        - Maybe excessive comments show that the chosen programming language does not support the design;
    - Duplicated code: similar code with slight differences in multiple places
        - D.R.Y
    - Long methods
    - Large classes (God classes, Blob classes, black hole classes)
    - Data classes: they have only data. No real functionality. Generally these classes would have getter and setters, but not much else;
    - Data clumps: groups of data appearing together in the instance variables of a class, or parameters to methods;
        - E.g., `public double calculateVolume(double x, double y, double z)`
            - We should have `public double calculateVolume(Point3D point)`
        - This can lead to `data classes` so make sure to use this wisely to not create more code smells, and make sure the class has effective methods, not just getters and setters;
    - Long parameter list
        - Use `parameter objects`;

- Code smells when making changes to the code (09):
    - Divergent change: occurs when we have to change a class in many different ways, for many different reasons;
        - Relates to the `god class smell`.
        - Poor separation of concerns is a common cause of this `code smell`;
        - If we have to change a class in multiple ways it is a good indicator that the responsabilities of this class should be broken up into separate classes. And these responsabilities should be extracted into their own classes. So the original class would delegate the responsabilities to the extracted classes;
    - Shotgun surgery: to make a small change we have to touch many classes;
        - Consider to move the many places that would have to be changed to one centralized class if that makes sense;
    - Feature envy: a method is more interested in the details of a class other than the one that it is in;
        - Consider putting them together;
    - Inappropriate intimacy: two classes talk really closely to each other (both classes call the other methods)
        - Consider creatin a middleware class an try to make this communication one-way only;
            - Sometimes it is not possible;
    - Law of demeter
        - Message chains: `getB().getC().doSomething();`
    - Primitive obsession: when we rely on built-in types too much (Ints, Longs, Floats, Strings);
        - Sometimes it is better to abstract a primitive type to an abstract type so we can make validations and effective methods;
    - Switch statements
    - Speculative Generality (Over-engineering): "We might need this someday"
        - Occurs when we make a superclass, interface, or code that is not needed at the time, but we thing we might need it someday;
        - We should practice `Just in time design`;
    - Refused bequest: When a subclass inherits something it does not need;
        - Check if the subclass really is a type of the base class. Maybe it makes more sense to have a standalone class or these unwanted bahaviors should not be defined in the superclass. If only some subclasses use these behaviors maybe they should be implemented in the subclasses only;

## Software Architecture

### Overview and Process
It provides higher productivity to the team

Always ask: Am I adding value to the client?

### Communicating Architecture

#### Kruchten's 4+1 Model View
Any view can be ommited if it is considered useless.

Or if two views look very similar they can be described together;

- Logical view: Focuses on the functional requirements. The context is the services that should be provided to end users;
    - Diagrams in this phase:
        - Class diagram: Shows the relationship between classes;
        - State diagram: Show the relationship between different states of the software;

- Process view: Focuses on non-functional requirements (performance, availability, etc.
    - Presents the processes implemented by the objects in the logical view;
    - It shows the execution order of method calls;
    - Synchronous or asynchronous behaviors must be described;
    - Diagrams involved:
        - Sequence diagram;
        - Activity diagram;
- Development view (Project management): Focused on the details of the software development and what is involved to support that;
    - Describes the hierarchical breakdown of the system into finer parts.
        - Systems -> subsystems -> components -> classes;
            - E.g.: messaging app(system) -> chat conversation list(subsystem) -> chat conversation(component) -> chat box(component) -> chat message(class);
    - Considers: Programming languages, libraries, toolsets...
    - This phase involves:
        - Scheduling
        - Budgets
        - Work assignemtns
- Physical view: Describes how the elements in the above views should be mapped to different nodes or hardware.
    - How they are deployed to different execution environments;
    - Diagrams involved:
        - Deployment diagram
- Scenarios: 
    - Scenarios relate elements in the 4 views to give a complete picture;
    - For each scenario there is a script that describes the sequence of interactions between objects and processes;
        - E.g: send a message to another user; view messages; view list of chats;
    - Each scenario will involve:
        - Key objects from logical view;
        - The processes in the process view;
        - The hierarchy in the development view;
        - The different nodes in the physical view;
    - Diagrams involved: Show how the other 4 views work together;
        - Use cases
        - User tasks

#### Component diagram
A component is an independent, encapsulated unit within a system;

Each component provides an interface to another component to interact with it;

Used to visualize how system's pieces interact and what relationships they have among them;

They are about high level structure;

Think of a pizza menu where we only have the title and ingredients, so we can have a better ideia of how they com together as a whole;

Elements:
- Ball connector - Provided interface: Shows that a component has an interface so other components can interact with it;
- Socket connector - Required interface: Shows that a component expects certain interface provided by some other component, to be able to achieve its responsibilities;

Steps:
- Identify the main objects in the system
- Identify the relevant libraries (third-party)
- Come up with the relationship between these components;

#### Package Diagram
Shows packages and the dependencies between them.

Groups elements that are related (based on data, classes other packages, or user tasks);

Defines a namespace for the elements within.

Name elements with a fully qualified name. `<namespace>.<element_name>`.

If the package has no elements to show in the package, its name should be centralized in the component element;

When details are needed we can place the package name in the tab and the element centralized or below. E.g.: interface Movement

Elements can be set as public or private;

Packages can:
- Import elements from another package;
- Import the whole content from another package;
- Be merged;

The relationship between elements is denoted by a dashed line with fulfilled arrow.
- The `<import>` tag defines the element to be accessed is public;
- The `<access>` tag defines the element to be accessed is private;
- The `<merge>` tag defines a merge;
    - Concept of generalization;
- The `<uses>` tag defines that a package A needs a package B for its full implementation. If there is no definition for package B there is no A;