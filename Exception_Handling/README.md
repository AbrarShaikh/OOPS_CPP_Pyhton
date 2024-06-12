# Exception Handling
- Exceptions are runtime anomalies or abnormal conditions that a program encounters during its execution.
- The process of handling these exceptions is called exception handling.

```try``` - code that may raise an exception.\
```catch``` - code that handles the exception thrown by the throw keyword.\
```throw``` - throws an exception when an error is detected (Optional).
```Cpp
try {         
     // Code that might throw an exception
     throw SomeExceptionType("Error message");
 } 
catch( ExceptionName e1 )  {   
     // catch block catches the exception that is thrown from try block
 }
```
example: throw in class
```Cpp
class AClass{ //a class
     public:
     class AnError //exception class{};
     void Func(){ //a member function
          if( /* error condition */ )
               throw AnError(); //throw exception}
};
////////////////////////////////////////////////////////////////
int main(){ //application
     try{ //try block
          AClass obj1; //interact with AClass objects
          obj1.Func(); //may cause error
     }
     catch(AClass::AnError) //exception handler
          { //(catch block)
          //tell user about error, etc.}
     return 0;}
```
### Multiple catch Statements
```Cpp
    try {     
        // throw exception if array out of bounds
        if (index >= 4)
            throw "Error: Array out of bounds!";
        .........................    
        // throw exception if denominator is 0
        if (denominator == 0)
            throw 0;
        '''''''''''''''''''''''''  }
    // catch "Array out of bounds" exception
    catch (const char* msg) {
        cout << msg << endl;}
    // catch "Divide by 0" exception
    catch (int num) {
        cout << "Error: Cannot divide by " << num << endl;}
    // catch any other exception
    catch (...) {
        cout << "Unexpected exception!" << endl;
    }
    return 0;   }
```
