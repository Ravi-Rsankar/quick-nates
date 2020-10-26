# Quick-notes: JavaScript

#### JS execution

hat the JS engine does when we run the code.

- JS Engine parses your code line by line & identifies variables & functions created by code (which will be used in the execution phase)
- JS Engine setup memory space for variables & functions ( called as **Hoisting**)

**Hoisting** is basically the JS Engine set-asides memory space for variables and functions used inside the code before your code is executed. These variables & functions comprise the Execution Context of any function that is being executed.

#### Call stack

JavaScript engine uses a **call stack** to manage [execution contexts](https://www.javascripttutorial.net/javascript-execution-context/): the Global Execution Context and Function Execution Contexts.

The call stack works based on the LIFO principle i.e., last-in-first-out.

When you execute a script, the JavaScript engine creates a Global Execution Context and pushes it on top of the call stack.

Whenever a function is called, the JavaScript engine creates a Function Execution Context for the function, pushes it on top of the Call Stack, and starts executing the function.

If a function calls another function, the JavaScript engine creates a new Function Execution Context for the function that is being called and pushes it on top of the call stack.

When the current function completes, the JavaScript engine pops it off the call stack and resumes the execution where it left off in the last code listing.

The script will stop when the call stack is empty.

#### Synchronous and Asynchronous

JavaScript is the **single-threaded** programming language. The JavaScript engine has only one call stack so that it only can do one thing at a time.

When executing a script, the JavaScript engine executes code from top to bottom, line by line. In other words, it is synchronous.

Asynchronous is the opposite of synchronous, which means happening at the same time. So how does JS manage to perform asynchronous operations?  **Callbacks**

#### Callbacks

In JavaScript, a callback is a [function](https://www.javascripttutorial.net/javascript-function/) passed into another function as an argument to be executed later. In JS, functions are objects, so we can pass function as object to other function and call that inside the outer function. 

A function which can be passed as an argument to the higher-order functions and can return function. The argument passed as a function to the higher-order function is called as a callback.

However, this callback strategy does not scale well when the complexity grows significantly.

Nesting many asynchronous functions inside callbacks is known as the **pyramid of doom** or the **callback hell**

```js
doSomething1(arg1, (err, data1) => {
  //some code...
  doSomethingAfter1(arg2, (err, data2) => {
    //some code
    doSomethingAfter2(arg3, (err, data2) => {
      //some code...
    });
  });
});
```

To avoid the pyramid of doom, you use [promises](https://www.javascripttutorial.net/es6/javascript-promises/) or [async/await](https://www.javascripttutorial.net/es-next/javascript-async-await/) functions.

#### Event Loop

The event loop is a constantly running process that monitors both the callback queue and the call stack.

If the call stack is not empty, the event loop waits until it is empty and places the next function from the callback queue to the call stack. If the callback queue is empty, nothing will happen

#### Promises

A promise is an object which keeps track of whether the asynchronous event has happened already or not and determines what happens after the event has occurred.

Instead of providing a callback, a promise has its own methods (resolved or rejected), which you call to tell the promise what will happen when it is successful or when it fails.

It can be in three states, fulfilled, pending or rejected. It helps to catch all the errors that occurred after rejection or attach a callback to the handle of the fulfilled value.

#### Boolean in JS

In javascript logical operators can be applied to non boolean values also. A condition true && "Hi" will execute without any errors. The result of the above command will be 'Hi', meaning both the conditions are true.

In javascript, empty string is evaluated as false when applied to a logical operator. Similarly the number 0 means false