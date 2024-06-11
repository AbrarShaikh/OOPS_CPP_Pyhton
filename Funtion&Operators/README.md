# Function Overloading
- two functions can have the same name if the number and/or type of arguments passed is different.
- These functions having the same name but different arguments are known as overloaded functions.
- Function cant be overloaded based on only different return Type. 

# Function OverRiding
- If derived class defines same function as defined in its base class, it is known as function overriding.
- member function in the derived class shadows the member function in the base class.
- It is used to achieve runtime polymorphism.
- 

# Friend Function
- can access the private and protected data of a class.
- function definition does not use either the keyword friend or scope resolution operator.
- It can be declared either in the private or the public part.
- It cannot be called using the object as it is not in the scope of that class.
- It can be invoked like a normal function without using the object.
```C
class Distance {
    private:
        int meter;
        
        // friend function
        friend int addFive(Distance);

    public:
        Distance() : meter(0) {}
        
};

// friend function definition
int addFive(Distance d) {

    //accessing private members from the friend function
    d.meter += 5;
    return d.meter;
}
```
# Friend Class
- A friend class can access both private and protected members of the class in which it has been declared as friend.
- all the member functions of the friend class become friend functions.
```C
class ClassB;

class ClassA {
    private:
        int numA;

        // friend class declaration
        friend class ClassB;

    public:
        // constructor to initialize numA to 12
        ClassA() : numA(12) {}
};

class ClassB {
    private:
        int numB;

    public:
        // constructor to initialize numB to 1
        ClassB() : numB(1) {}
    
    // member function to add numA
    // from ClassA and numB from ClassB
    int add() {
        ClassA objectA;
        return objectA.numA + numB;
    }
};
```
