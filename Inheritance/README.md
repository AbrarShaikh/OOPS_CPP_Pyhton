# Inheritance
-  allows to create a new class (derived class) from an existing class (base class).
-  derived class inherits the features from the base class and can have additional features of its own
-  Inheritance is an ```is-a relationship```. We use inheritance only if an is-a relationship is present between the two classes.

```Cpp
class  <derived_class_name> : <access-specifier> <base_class_name>
{ //body}
```
### Access Modes
- _public_: members of the base class are inherited by the derived class __as it is__.
- _private_:  __All__ the members of the base class become __private__ members in the derived class.
- _protected_: The __Public__ members of the base class become __protected__ members in the derived class.
- private members of the base class are always private in the derived class.

## Multilevel Inheritance
```cpp
class A {
public:
    void display() {
        cout<<"Base class content.";}
};
class B : public A {};
class C : public B {};
```

## Multiple Inheritance
- class can be derived from more than one parent.
- Ambiguity : problem occurs during function overriding when parents are derived from same grade parent class.
```cpp
class A{
  public:
    void func();};
class B : public A  
  { };
class C : public A
  { };
class D : public B, public C //same subobjects (2 copies of parent) --> Error
  { };
```

### Virtual Inheritance
- ```Virtual Base Class``` makes sure that the grandchild derived classes inherit only one copy of a base class's member variables.
```cpp
class A{ 
  public:
    void func();};
class B : virtual public A  
  { };
class C : virtual public A
  { };
class D : public B, public C //shares only one copy of parent
  { };
```
