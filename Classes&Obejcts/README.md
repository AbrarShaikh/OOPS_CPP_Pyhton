# Constructor
- constructor is a special method which is invoked automatically at the time of object creation.
- It is used to initialize the data members of new object generally.
- The constructor in C++ has the same name as class or structure.

## Default constructor
- A constructor which has no argument is known as default constructor.
- It is invoked at the time of creating object.
```Cpp
class  Wall {
  private:
    double length;

  public:
    // default constructor to initialize variable
    Wall()
      : length{5.5} {
      cout << "Creating a wall." << endl;
      cout << "Length = " << length << endl;
    }
};
```
### Defaulted Constructor
``` Cpp
class  Wall {
  private:
    double length {5.5};

  public:
    // defaulted constructor to initialize variable
    Wall() = default;
    
    void print_length() {
    	cout << "length = " << length << endl;
    }
};
```
## Parameterized Constructor
- It is used to provide different values to distinct objects.
```Cpp
class Wall {
  private:
    double length;
    double height;

  public:
    // parameterized constructor to initialize variables
    Wall(double len, double hgt)
      : length{len}
      , height{hgt} {
    }

    double calculateArea() {
      return length * height;
    }
};
```
### Member Initializer List
```
: length{len} 
, height{hgt}
```
Or
```
: length(len)
, height(hgt)
```
## Constructor Overloading
```Cpp
class Room {
   private:
    double length;
    double breadth;

   public:
    // 1. Constructor with no arguments
    Room() {
        length = 6.9;
        breadth = 4.2;
    }

    // 2. Constructor with two arguments
    Room(double l, double b) {
        length = l;
        breadth = b;
    }
    // 3. Constructor with one argument
    Room(double len) {
        length = len;
        breadth = 7.2;
    }
```

## Copy Constructor
- Copy constructor is an overloaded constructor
- used to declare and initialize an object from another object of same class.
- used to copy data from one object to another.
#
Copy Constructor is called when:
1. initialize the object with another existing object of the same class type.
2. the object of the same class type is passed by value as an argument.
3. the function returns the object of the same class type by value.
###  Implicit Copy Constructor
``` Cpp
class Sample {
    int id;
 
public:
    // parameterized constructor
    Sample(int x) { id = x; }
    void display() { cout << "ID=" << id; }
};
```
``` Cpp
    Sample obj1(10);
    obj1.display(); 
    // creating an object of type Sample from the obj
    Sample obj2(obj1), obj3=obj1;
    obj2.display();
```
###  Explicit Copy Constructor
``` Cpp
class Wall {
  private:
    double length;
    double height;

  public:

    // initialize variables with parameterized constructor
    Wall(double len, double hgt)
      : length{len}
      , height{hgt} {
    }

    // copy constructor with a Wall object as parameter
    // copies data of the obj parameter
    Wall(const Wall& obj)
      : length{obj.length}
      , height{obj.height} {
    }

    double calculateArea() {
      return length * height;
    }
};
```
```Cpp
  // create an object of Wall class
  Wall wall1(10.5, 8.6);
  // copy contents of wall1 to wall2
  Wall wall2 = wall1;
```
Two types of copies are produced by the constructor:
### Shallow Copy
- The default copy constructor can only produce the shallow copy.
- The default constructor creates the exact copy or shallow copy of the existing object.
- A Shallow copy is defined as the process of creating the copy of an object by copying data of all the member variables as it is, except dynamically allocated memory from heap section.
- If some variables are dynamically allocated memory from heap section, then the copied object variable will also reference the same memory location.
- This will create ambiguity and run-time errors, dangling pointer.
- in Above Sample class example, obj1 and obj2 are Shallow Copy.

### Deep Copy
- user-defined (Explicit) constructor that creates the Deep copy.
- Deep copy dynamically allocates the memory for the copy and then copies the actual value
- both the source and copy have distinct memory locations.

# Destructors
- A destructor is a special member function that is called automatically when an object goes out of scope or when we delete the object with the delete expression.
- destructor has the same name as that of the class, and it does not have a return type.
- ~ precedes the identifier to indicate destructor.
``` Cpp
class Wall {
  private:
    double* length;
    double* height;

  public:
    ~Wall() {
        delete length;
        delete height;
    }
};
```
### Private Destructors
- For dynamically created objects, it may happen that you pass a pointer to the object to a function and the function deletes the object.
- If the object is referred after the function call, the reference will become dangling.
```Cpp
class Test {
private:
    ~Test() {}
};
int main() { Test* t = new Test; }
```
- it is the programmer’s responsibility to delete it. So compiler doesn’t bother.
- but ```delet t``` program fails in the compilation When delete, destructor is called.\
Can be resolved using
1. function as a friend of the class
```Cpp
class Test {
private:
    ~Test() {}
 
public:
    friend void destructTest(Test*);
};
 
// Only this function can destruct objects of Test
void destructTest(Test* ptr) { delete ptr; }
```
2.  class instance method
```Cpp
class parent {
    // private destructor
    ~parent() { cout << "destructor called" << endl; }
 
public:
    parent() { cout << "constructor called" << endl; }
    void destruct() { delete this; }
};
int main()
{
    parent* p;
    p = new parent;
    // destructor called
    p->destruct();
 
    return 0;
}
```
# Access Modifiers
### Public: 
- All the class members declared under the public specifier will be available to everyone
### Private: 
- The class members declared as private can be accessed only by the member functions inside the class.
- friend classes and friend functions can access private members.
### Protected
- can be accessed within the class and from the derived class.

| Specifiers	| Same Class |	Derived Class	| Outside Class |
| :--- | :---: | :---: | :---: |
| public	| Yes	| Yes	| Yes |
| private	| Yes	| No	| No |
| protected	| Yes	| Yes |	No |
