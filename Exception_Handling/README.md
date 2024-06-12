# Exception Handling
- Exceptions are runtime anomalies or abnormal conditions that a program encounters during its execution.
- The process of handling these exceptions is called exception handling.

```try``` - code that may raise an exception.\
```catch``` - code that handles the exception thrown by the throw keyword.\
```throw``` - throws an exception when an error is detected (Optional).
```C
try {         
     // Code that might throw an exception
     throw SomeExceptionType("Error message");
 } 
catch( ExceptionName e1 )  {   
     // catch block catches the exception that is thrown from try block
 }
```
