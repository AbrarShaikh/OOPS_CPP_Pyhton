# Function Overloading
- two functions can have the same name if the number and/or type of arguments passed is different.
- These functions having the same name but different arguments are known as overloaded functions.
- Function cant be overloaded based on only different return Type. 

# Function OverRiding
- If derived class defines same function as defined in its base class, it is known as function overriding.
- member function in the derived class shadows the member function in the base class.
- redefinition of base class function in its derived class with the same signature
- It is used to achieve Compile time as well as Runtime polymorphism.
### Compile time overriding
- call to the overridden function is resolved during compile time.
- It is also called early binding (static binding) where the function call is binded to its definition during compilation.
```C
class Base {
   public:
    void print() {
        cout << "Base Function" << endl;
    }
};

class Derived : public Base {
   public:
    void print() {
        cout << "Derived Function" << endl;
    }
};
```
```
    Derived derived1, derived2;
    derived1.print();

    // access print() function of the Base class
    derived2.Base::print();
```
###  Runtime overriding using Virtual Function
- function call will be binded to its definition during runtime (also known as late binding or dynamic binding).
- This can be done with the help of virtual functions.

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