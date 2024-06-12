# Operator Overloading
- Operator overloading is a compile-time polymorphism.
- ```operator``` - a special keyword
- ability to provide the operators with a special meaning for a data type, this ability is known as operator overloading.
- For operator overloading to work, at least one of the operands must be a user-defined class object.
- 

### Operators that cannot be overloaded. 
```
sizeof
typeid
Scope resolution (::)
Class member access operators (.(dot), .* (pointer to member operator))
Ternary or conditional (?:)
```

syntax
```C
returnType operator symbol (arguments) {
    ... .. ...
} 
```

### Overload Operators using a Member Function
- at least one of the operands must be a user-defined class object.
- class member that defines the operator function must be one of the operands.
- Any compatible type, including additional user-defined types, may be used for the other operand.
``` C
class Complex{
  …..
   public: 
      Complex operator + (const Complex& obj){
          Complex temp;
           temp.real = real + obj.real;
           temp.img = img + obj.img;
           return temp;}
  …….
};
```
```
Complex c3 = c1 + c2; --> c1.operator+(c2);
```

### Overload Operators Using Friend Function
- The problem with this approach is, not all the time the first operand is an object of a user-defined type.
- Friend functions can overload operators for user-defined types without altering the class declaration because they are not class members.
- This is helpful when you need help editing the original class.
- friend function is not a member of the class, it does not have a ```this``` pointer.
- Therefore, an overloaded friend operator function is passed the operands explicitly.
```
c2 = 1 + c1;
```
``` C
class Complex {
    private:
        float real;
        float img;
    public:
         // constructor to initialize real and img to 0
         Complex() : real(0), img(0) {}
         Complex(float real, float img) : real(real), img(img){}
       // overload the + operator
         friend Complex operator + (const Complex& obj1, const Complex& obj2) {
             Complex temp;
              temp.real = obj1.real + obj2.real;
              temp.img = obj1.img + obj2.img;
              return temp;    }
    void display() {
        if (img < 0)
            cout << "Output Complex number: " << real << img << "i";
      else
           cout << "Output Complex number: " << real << "+" << img << "i";   }};
```
