# Data Abstraction 
- Data abstraction refers to providing only essential information about the data to the outside world, hiding the background details or implementation.
- Hiding internal details and showing functionality.
- Abstraction is achieved by __interfaces__ and abstract classes.
- Classes are ADT-abstract data types.
- The abstract method contains only method declaration but not implementation.
- it reduces __complexity__, isolates impact of change

# Encapsulation
- Binding (or wrapping) code and data together into a single unit (Class) is known as encapsulation.
- It is the mechanism that binds together code and the data it manipulates.
- Encapsulation is a method to hide the data in a single entity or unit along with a method to protect information from outside world.
- This method encapsulates the data and function together inside a class which also results in data abstraction. 
- Data encapsulation is most __strick__ feature of class.
- Encapsulation also leads to data abstraction or data hiding.
- Data (access specifier = private) is not accessible to the outside world.
- In encapsulation, the data in a class is hidden from other classes, which is similar to what data-hiding.
- it reduces __complexity__, increases __security__ and __reusibility__.

# Inheritance
- Inheritance allows us to create a new class (derived class) from an existing class (base class).
- one object acquires all the properties and behaviours of the parent object.
- It supports conecpt of __hieratchical classicfication__.
- Eliminates __redundencies__, increases __resuibilty__ by extending use of existing class.
- It is basically applied to classes.

# Polymorphism
- Polymorphism means "many forms", and it occurs when we have many classes that are related to each other by inheritance.
- differentiate between entities with the same name efficiently.
- Different situations may cause an operation to behave differently. The type of data utilized in the operation determines the behaviour.
- it is basically applied to functions or methods.
- polymorphism is implemented with the help of Compile time polymorphism (function overloading, operator overloading), and Run time polymorphism (function overriding) and virtual functions.

# Dynamic Binding
- code to be executed in response to the function call is decided at runtime.
- code associated with a given procedure call is not known until the time of the call at run time.
- function call associated with Polymorphic reference depends on the dynamic type of that reference.
- at runtime, the code matching with the object under the current reference will be called.
- C++ has virtual functions to support this.
- Dynamic Method Binding One of the main advantages of inheritance and associated with Polymorphism.

# Message Passing
- A message for an object is a request for the execution of a procedure and therefore will invoke a function in the receiving object that generates the desired results.
- Message passing involves specifying the name of the object, the name of the function, and the information to be sent.
```
object.classMethod(info)
```
