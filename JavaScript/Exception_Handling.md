# Exception handling
Exception handling in Javascript is one of the powerful features for handling errors and helps to avoid the sudden crashes of our programs and applications. Additionally, it helps to maintain the normal flow of our programs.

As the name suggests, **Exception handling** is made up of two words. The first word **Exception** is known as an unexpected or abnormal condition that occurs during the runtime or execution of a program. And second-word handling means how we can handle those unusual situations.

Exception handling in Javascript is the process of handling abnormal statements that occur during the execution of a program.

And it also helps in tracking errors, which means that the exception explains why the error occurred and when and where it happened in the code.

**The fundamental causes of exception errors are:**
* Whenever we try to divide any numbers by 0, this leads to infinity, and as a result, the exceptions are shown.
* When we try to call any files that don’t exist within our system.
* When the input provided by the user is wrong.
* When our network connection is down.

## Types of Errors
During the execution of JavaScript code, three types of errors can occur:-
### 1. Syntax error
### 2. Runtime error
### 3. Logical error

### 1. Syntax error
Syntax errors appear when the user makes a mistake in the predefined syntax of the javascript language. The interpreter cannot interpret this error raised during the code compilation.
These errors are:

* Spelling errors (wrong spelling, such as fiction instead of function).
* Ignoring essential characters, such as failing to use a semicolon to end a statement.
* Incorrect indentation or formatting
And most importantly, these errors stop the program from working until we correct the mistake.

### 2. Runtime Error:-
Runtime Error occurs during the program's execution and gets detected only when you run the program; that's why it's known as a runtime error. And these errors suddenly crash the program or applications, and that's where exception handling became useful, and via the help of it, we can maintain the normal flow of the program.
These types of errors occur when:-

* This is caused by scenarios such as division by 0 and integer overflow.
* Runtime error is also caused by the segmentation faults such as Accessing an array out of bound.
As a developer, it's your responsibility to handle these types of errors.

### 3. Logical Error:- 
Logical Error occurs when there is any logical mistake in the program that may not produce the desired output and may terminate abnormally. These types of errors do not throw an error message or an exception.

The reason is that the code is showing the result but not doing the same thing the developer intends. Unfortunately, finding logical errors can be challenging, and you must go through manual testing to detect these types of errors.

## Error Object
Whenever an error occurs during the execution or runtime of the program, the code stops unexpectedly, and JavaScript raises an exception scenario with the Error object thrown by the throw statement.

The error object is thrown by JavaScript, or the user can create a user-defined error object with the help of the throw statement.

The error object has two main properties:

**name**:- error name stores or returns the name of the error.

**Message**:- Whereas error message gives or describes the error message in string form in JavaScript.
Although the error is a generic constructor as it gives basic information about the condition, on the other hand, various standard built-in error types or error constructors are the foundation of exception handling in javascript as they provide detailed information about the problem.


### Exception Handling Statements
An exception is an abnormal or unexpected condition that occurs during the runtime, and javascript provides various statements or a combination of statements to handle the exceptions.

It handles exceptions in try-catch-finally statements and throws statements.

Before we explore each statement, let's get a basic understanding of these terms:

**try{}:-** 

The try block will contain the code, which may cause exceptions during the execution. If any errors occur, It stops the execution immediately and passes the control to the catch block.

**catch{}:-**

The catch block contains the code that will only execute when the errors occur in the corresponding try block. If the try block is executed successfully, then the catch block will be ignored.

**finally{}:-** 

The code placed inside the "finally" block will be executed whether an error has occurred or not.

**throw:-** 

The throw keyword or statement is used for throwing custom or user-defined errors.
Now that you know about all these let us move ahead and discuss exception handling statements.

## Throw Statements
The throw keyword is used to throw custom or user-defined errors, which means you can create an error object with the message and name property. Additionally, you can use anything as an error object, maybe even a primitive, like a number or a string.
The syntax is:
```javascript
throw <error object>
```
```javascript
function myFunc(x,y) {

         try {
            if ( y == 0 ) { // checking for divide by zero condition
                throw( "Divide by zero error." ); // If condition is true than throwing custom error
            } else {
                var c = x / y;
                console.log(c); 
            }
        }
        catch ( e ) { // catching error generated by throw
            console.log("Error: " + e ); 
        }
    }
            

```
## Try…catch Statements
The try block contains the code that will be executed successfully if no exceptions occur. Still, in the case of an exception or error, code execution in the try block stops immediately and passes the control to the catch block.

The catch block contains code that will only be executed when the try block throws an exception. You want to succeed in the try block, but if it does not succeed and generates an error, the catch block takes control and takes care of that situation.

In general, if the try block is executed successfully, the catch block will be ignored without causing any issues.

```javascript
try {
  // code
} catch (err) {
  // Code only executes if try throws an exception
}

```

In the above, we have the try-and-catch blocks that contain some code.

* The execution of the code started and worked fine till line number 3, and then found a function that was not defined in the code.
* it stops the execution and passes the control to the "catch" because the try throws an exception.
* The catch block then prints the error on the console.

### try…catch…finally Statements
The try and catch block is executed based on certain things; the try block will be executed until it encounters an error, and the catch block is only executed when the try block throws an exception. But "finally block" doesn't care about both blocks.

In general, the " finally block" will be executed whether an error has occurred or not.

The syntax is:
```javascript
try {
   // try to execute the code inside of it
} catch (err) {
   // take care of errors (execution depends on the try block)
} finally {
   // Don't care about anything always going to execute
}

```



