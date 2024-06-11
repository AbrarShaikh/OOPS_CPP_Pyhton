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

## Copy Constructor
- Copy constructor is an overloaded constructor
- used to declare and initialize an object from another object of same class.
- used to copy data from one object to another.
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
