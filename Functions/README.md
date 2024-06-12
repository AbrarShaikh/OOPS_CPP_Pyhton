# Friend Function
- can access the private and protected data of a class.
- function definition does not use either the keyword friend or scope resolution operator.
- It can be declared either in the private or the public part.
- It cannot be called using the object as it is not in the scope of that class.
- It can be invoked like a normal function without using the object.
```Cpp
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
```Cpp
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
- It is also called ```Early binding``` (```static binding```) where the function call is binded to its definition during compilation.
```Cpp
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
- function call will be binded to its definition during runtime (also known as ```late binding``` or ```dynamic binding```).
- This can be done with the help of virtual functions.

# Virtual Function 
- virtual function is a member function in the base class that you redefine in a derived class.
- It is used to tell the compiler to perform dynamic linkage or late binding on the function.
- In late binding function call is resolved during runtime. Therefore type of object are determined at runtime, and then binds the function call.
- They are accessed through ```object pointers```.
- A virtual function must be defined in the base class, even though it is not used.
- The prototypes of a virtual function of the base class and all the derived classes must be identical.
- We cannot have a virtual constructor, but we can have a virtual destructor.
- Virtual functions are useful when we store a group of objects.
- ```Override``` specifier specifies the member functions of the derived classes that override the member function of the base class.
Use : base class pointer can only access the base class members but not the members of the derived class.
Although C++ permits the base pointer to point to any object derived from the base class, it cannot directly access the members of the derived class.
```Cpp
class Base {
   public:
    virtual void print() {
        cout << "Base Function" << endl;
    }
};

class Derived : public Base {
   public:
    void print() override {
        cout << "Derived Function" << endl;
    }
};

int main() {
    Derived derived1;
    // pointer of Base type that points to derived1
    Base* base1 = &derived1;
    // calls member function of Derived class
    base1->print();
    return 0;}
```
# Abstract Class
- class that contains a pure virtual function is known as an abstract class.
- Pure Virtual function is one with ```expression = 0```
- We cannot create (instantiate) objects of an abstract class.
- However, we can derive classes from them, and use their data members and member functions (except pure virtual functions).
```Cpp
// Abstract class
class Shape {
   protected:
    float dimension;

   public:
    void getDimension() {
        cin >> dimension;
    }

    // pure virtual Function
    virtual float calculateArea() = 0;
};
// Derived class
class Square : public Shape {
   public:
    float calculateArea() {
        return dimension * dimension;
    }
};
// Derived class
class Circle : public Shape {
   public:
    float calculateArea() {
        return 3.14 * dimension * dimension;
    }
};
```
## Pure Virtual Function
- When the function has no definition, such function is known as "do-nothing" function, also known as a pure virtual function.
- implementation of all functions cannot be provided in a base class because of implementation is unknown. Such a class is called an abstract class.
- A virtual function is not used for performing any task. It only serves as a placeholder.
- class containing the pure virtual function cannot be used to declare the objects of its own, such classes are known as ```abstract base classes```.
- A pure virtual function or ```abstract function``` is a virtual function for which we can have an implementation, But we must override that function in the derived class.
- The main objective of the base class is to provide the traits to the derived classes and to create the base pointer used for achieving the runtime polymorphism.
```Cpp
class Base {
public:
    // pure virtual function
    virtual void show() = 0;
};
 
class Derived : public Base {
public:
    // implementation of the pure virtual function
    void show() { cout << "In Derived \n"; }
};
 
int main(void){
    // creating a pointer of type
    // Base pointing to an object
    // of type Derived
    Base* bp = new Derived();
    // calling the show() function using the
    // pointer
    bp->show();
    return 0;}
```
## Virtual Destructor
- When a derived class involves dynamic memory allocation, we have to deallocate the memory in its destructor.
- instance while deleting instances of the derived class using a base class pointer object.
- Deleting a derived class object using a pointer of base class type that has a non-virtual destructor results in undefined behavior.
```Cpp
class base {
  public:
    base()     
    { cout << "Constructing base\n"; }
    virtual ~base()
    { cout << "Destructing base\n"; }     
};
 
class derived : public base {
  public:
    derived()     
    { cout << "Constructing derived\n"; }
    ~derived()
    { cout << "Destructing derived\n"; }
}; 
int main(){
  base *b = new derived();  
  delete b;
  getchar();
  return 0;}
```
# Virtual Base class
- Virtual base classes are used in virtual inheritance in a way of preventing multiple “instances” (copy) of a given class appearing in an inheritance hierarchy when using multiple inheritances.
- Virtual Class is defined by writing a keyword “virtual” in the derived classes, allowing only one copy of data to be copied to Class B and Class C
- To prevent the error and let the compiler work efficiently. It saves space and avoids ambiguity.
- When a class is specified as a virtual base class, it prevents duplication of its data members. Only one copy of its data members is shared by all the base classes that use the virtual base class.
```Cpp
class A { 
public: 
    int a; 
    A() // constructor 
        a = 10; }; 
class B : public virtual A { }; //shares copy of A  
class C : public virtual A { }; //shares copy of A
class D : public B, public C { }; 
```
