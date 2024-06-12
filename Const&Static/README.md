# Static Data Member
- It is initialized to zero when the first object of its class is created. No other initialization is permitted.
- Only one copy of that member is created for the entire class and is ```shared``` by all the objects of that class, no matter how many objects are created.
- It is visible only within the class, but its lifetime is the entire program.
- ```Decleartion``` appers inside Class, but ```Defined``` outside of Class.

# Static Member Function
- A static function can have access to only other static members (functions or variables) declared in the same class.
- A static member function can be called using the class name (instead of its objects).

```C
class foo{
  private:
    static int count; //only one data item for all objects
    //note: “declaration” only!  
  public:
    foo() //increments count when object created
      { count++; }
  int getcount() //returns count
    { return count; }
  static void showcount()
    { cout<<"count is" << count; }
};
//--------------------------------------------------------------
int foo::count; //*definition* of count
//--------------------------------------------------------------
```

# const Member Functions
- If a member function does not alter any data in the class, then we may declare it as a const member function
```C
<type> function(args) const;
```
example:
```C
class aClass{
  private:
    int alpha;
  public:
    void nonFunc() //non-const member function
      { alpha = 99; } //OK
    void conFunc() const //const member function
      { alpha = 99; } //ERROR: can’t modify a member
};
```
# const Member Functions Arguments
```C
<type> function(const <type>args);
```
example:
```C
class Distance //English Distance class{
  private:
    int feet;
    float inches;
  public: //constructor (no args)
    Distance() : feet(0), inches(0.0)
      { } //constructor (two args)
    Distance(int ft, float in) : feet(ft), inches(in)
      { }

  Distance add_dist(const Distance&) const; //add };
//--------------------------------------------------------------
Distance Distance::add_dist(const Distance& d2) const
{
Distance temp; //temporary variable
 feet = 0; //ERROR: can’t modify this
 d2.feet = 0;} //ERROR: can’t modify member
```
