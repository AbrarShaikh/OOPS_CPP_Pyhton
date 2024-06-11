# Constructor
- constructor is a special method which is invoked automatically at the time of object creation.
- It is used to initialize the data members of new object generally.
- The constructor in C++ has the same name as class or structure.

## Default constructor
- A constructor which has no argument is known as default constructor.
- It is invoked at the time of creating object.
```C
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
``` C
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
```C
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
```C
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
``` C
class Sample {
    int id;
 
public:
    // parameterized constructor
    Sample(int x) { id = x; }
    void display() { cout << "ID=" << id; }
};
```
``` C
    Sample obj1(10);
    obj1.display(); 
    // creating an object of type Sample from the obj
    Sample obj2(obj1), obj3=obj1;
    obj2.display();
```
###  Explicit Copy Constructor
``` C
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
```C
  // create an object of Wall class
  Wall wall1(10.5, 8.6);
  // copy contents of wall1 to wall2
  Wall wall2 = wall1;
```
Two types of copies are produced by the constructor:
### Shallow Copy
- The default copy constructor can only produce the shallow copy.
- The default constructor creates the exact copy or shallow copy of the existing object
- A Shallow copy is defined as the process of creating the copy of an object by copying data of all the member variables as it is.
- in Above Sample class example, obj1 and obj2 are Shallow Copy.

### Deep Copy
- user-defined (Explicit) constructor that creates the Deep copy.
- Deep copy dynamically allocates the memory for the copy and then copies the actual value
- both the source and copy have distinct memory locations.

# Destructors
- A destructor is a special member function that is called automatically when an object goes out of scope or when we delete the object with the delete expression.
- destructor has the same name as that of the class, and it does not have a return type.
- ~ precedes the identifier to indicate destructor.
``` C
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
