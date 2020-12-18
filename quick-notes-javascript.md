# Quick-notes: JavaScript

## JS execution

hat the JS engine does when we run the code.

- JS Engine parses your code line by line & identifies variables & functions created by code (which will be used in the execution phase)
- JS Engine setup memory space for variables & functions ( called as **Hoisting**)

**Hoisting** is basically the JS Engine set-asides memory space for variables and functions used inside the code before your code is executed. These variables & functions comprise the Execution Context of any function that is being executed.

## Call stack

JavaScript engine uses a **call stack** to manage [execution contexts](https://www.javascripttutorial.net/javascript-execution-context/): the Global Execution Context and Function Execution Contexts.

The call stack works based on the LIFO principle i.e., last-in-first-out.

When you execute a script, the JavaScript engine creates a Global Execution Context and pushes it on top of the call stack.

Whenever a function is called, the JavaScript engine creates a Function Execution Context for the function, pushes it on top of the Call Stack, and starts executing the function.

If a function calls another function, the JavaScript engine creates a new Function Execution Context for the function that is being called and pushes it on top of the call stack.

When the current function completes, the JavaScript engine pops it off the call stack and resumes the execution where it left off in the last code listing.

The script will stop when the call stack is empty.

## Synchronous and Asynchronous

JavaScript is the **single-threaded** programming language. The JavaScript engine has only one call stack so that it only can do one thing at a time.

When executing a script, the JavaScript engine executes code from top to bottom, line by line. In other words, it is synchronous.

Asynchronous is the opposite of synchronous, which means happening at the same time. So how does JS manage to perform asynchronous operations?  **Callbacks**

## Callbacks

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

## Event Loop

The event loop is a constantly running process that monitors both the callback queue and the call stack.

If the call stack is not empty, the event loop waits until it is empty and places the next function from the callback queue to the call stack. If the callback queue is empty, nothing will happen

## Promises

A promise is an object which keeps track of whether the asynchronous event has happened already or not and determines what happens after the event has occurred.

Instead of providing a callback, a promise has its own methods (resolved or rejected), which you call to tell the promise what will happen when it is successful or when it fails.

It can be in three states, fulfilled, pending or rejected. It helps to catch all the errors that occurred after rejection or attach a callback to the handle of the fulfilled value.

## Boolean in JS

In JavaScript logical operators can be applied to non Boolean values also. A condition true && "Hi" will execute without any errors. The result of the above command will be 'Hi', meaning both the conditions are true.

In JavaScript, empty string is evaluated as false when applied to a logical operator. Similarly the number 0 means false

## Array functions

##### map

The map() method **creates a new array** populated with the results of calling a provided function on every element in the calling array.

```js
const array1 = [1, 4, 9, 16];
// pass a function to map
const map1 = array1.map(x => x * 2);

console.log(map1);
// expected output: Array [2, 8, 18, 32]

```

Since `map` builds a new array, using it when you aren't using the returned array is an anti-pattern; use `forEach` or `for-of` instead.

You shouldn't be using `map` if:

- you're not using the array it returns; and/or
- you're not returning a value from the callback.

##### forEach

The forEach() method executes a provided function once for each array element. The callback function does not expect a return value, and the forEach() method itself also returns undefined.

```js
const array1 = ['a', 'b', 'c'];

array1.forEach(element => console.log(element));

// expected output: "a"
// expected output: "b"
// expected output: "c"
```

##### filter

The **`filter()`** method **creates a new array** with all elements that pass the test implemented by the provided function. We call this type of callback a predicate function.

```js
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

const result = words.filter(word => word.length > 6);

console.log(result);
// expected output: Array ["exuberant", "destruction", "present"]

```

##### find

The find() method behaves similarly to the filter() method, but it only returns a single element. This method will stop at the first element that "pass the test", and return that. If none exists, it will return undefined.

```js
const array1 = [5, 12, 8, 130, 44];

const found = array1.find(element => element > 10);

console.log(found);
// expected output: 12
```

##### findIndex

The **`findIndex`** method returns the **index** of the first element in the array **that satisfies the provided testing function**. Otherwise, it returns `-1`, indicating that no element passed the test.

```js
const array1 = [5, 12, 8, 130, 44];

const isLargeNumber = (element) => element > 13;

console.log(array1.findIndex(isLargeNumber));
// expected output: 3

```

##### reduce

The reduce() method takes a callback with (at least) two arguments: An accumulator and the current element. For each iteration, the return value of the callback function is passed on as the accumulator argument of the next iteration and ultimately becomes the final, single resulting value.

```js
const array1 = [1, 2, 3, 4];
const reducer = (accumulator, currentValue) => accumulator + currentValue;

// 1 + 2 + 3 + 4
console.log(array1.reduce(reducer));
// expected output: 10

// 5 + 1 + 2 + 3 + 4
console.log(array1.reduce(reducer, 5));
// expected output: 15

```

##### some

The some() method takes a predicate function and return **true** if any of the elements in the array "passes the test".  Otherwise, false

```js
const array = [1, 2, 3, 4, 5];

// checks whether an element is even
const even = (element) => element % 2 === 0;

console.log(array.some(even));
// expected output: true

```

##### every

The **`every()`** method tests whether all elements in the array pass the test implemented by the provided function. It returns a Boolean value.

```js
const isBelowThreshold = (currentValue) => currentValue < 40;

const array1 = [1, 30, 39, 29, 10, 13];

console.log(array1.every(isBelowThreshold));
// expected output: true
```

##### includes

The **`includes`** method determines whether an array includes a certain value among its entries, returning `true` or `false` as appropriate.

```js
const array1 = [1, 2, 3];

console.log(array1.includes(2));
// expected output: true

const pets = ['cat', 'dog', 'bat'];

console.log(pets.includes('cat'));
// expected output: true

console.log(pets.includes('at'));
// expected output: false
```

##### fill

The `fill` method changes all elements in an array to a static value, from a start index (default `0`) to an end index (default `array.length`). It returns the modified array.

```js
const array1 = [1, 2, 3, 4];

// fill with 0 from position 2 until position 4
console.log(array1.fill(0, 2, 4));
// expected output: [1, 2, 0, 0]

// fill with 5 from position 1
console.log(array1.fill(5, 1));
// expected output: [1, 5, 5, 5]

console.log(array1.fill(6));
// expected output: [6, 6, 6, 6]
```

##### reverse

The **`reverse()`** method reverses an array *in place* (without creating extra storage). The first array element becomes the last, and the last array element becomes the first.

```js
const array1 = ['one', 'two', 'three'];
console.log('array1:', array1);
// expected output: "array1:" Array ["one", "two", "three"]

const reversed = array1.reverse();
console.log('reversed:', reversed);
// expected output: "reversed:" Array ["three", "two", "one"]

// Careful: reverse is destructive -- it changes the original array.
console.log('array1:', array1);
// expected output: "array1:" Array ["three", "two", "one"]

```

##### flat

The `flat()` method creates a new array with all sub-array elements concatenated into it recursively up to the specified depth. The default depth is 1.

```js
const arr1 = [0, 1, 2, [3, 4]];

console.log(arr1.flat());
// expected output: [0, 1, 2, 3, 4]

const arr2 = [0, 1, 2, [[[3, 4]]]];

console.log(arr2.flat(2));
// expected output: [0, 1, 2, [3, 4]]

```

##### flatMap

The flatMap() method applies a callback to each element of the array and then flatten the result into an array. It combines flat() and map() in one function.

```js
const numbers = [[1],[2],[3],[4],[5]]
const flattenedDoubles = numbers.flatMap(n => n*2)
console.log(flattenedDoubles)
```

A new array with each element being the result of the callback function and flattened to a depth of 1.

##### sort

The sort() method is used to sort the elements of an array and returning the sorting array. Be aware that this method is mutating the original array. The default sort order is ascending.

```js
const months = ['March', 'Jan', 'Feb', 'Dec'];
months.sort();
console.log(months);
// expected output: Array ["Dec", "Feb", "Jan", "March"]

const array1 = [1, 30, 4, 21, 100000];
array1.sort();
console.log(array1);
// expected output: Array [1, 100000, 21, 30, 4]

```

##### pop

The **`pop()`** method removes the **last** element from an array and returns that element. This method changes the length of the array.

```js
const plants = ['broccoli', 'cauliflower', 'cabbage', 'kale', 'tomato'];

console.log(plants.pop());
// expected output: "tomato"

console.log(plants);
// expected output: Array ["broccoli", "cauliflower", "cabbage", "kale"]

plants.pop();

console.log(plants);
// expected output: Array ["broccoli", "cauliflower", "cabbage"]

```

##### shift

The `shift()` method removes the **first** element from an array and returns that removed element. This method changes the length of the array.

```js
const array1 = [1, 2, 3];

const firstElement = array1.shift();

console.log(array1);
// expected output: Array [2, 3]

console.log(firstElement);
// expected output: 1

```

##### push

The `push()` method adds one or more elements to the end of an array and returns the new length of the array.

```js
const animals = ['pigs', 'goats', 'sheep'];

const count = animals.push('cows');
console.log(count);
// expected output: 4
console.log(animals);
// expected output: Array ["pigs", "goats", "sheep", "cows"]

animals.push('chickens', 'cats', 'dogs');
console.log(animals);
// expected output: Array ["pigs", "goats", "sheep", "cows", "chickens", "cats", "dogs"]

```

##### unshift

The `unshift()` method adds one or more elements to the beginning of an array and returns the new length of the array.

```js
const array1 = [1, 2, 3];

console.log(array1.unshift(4, 5));
// expected output: 5

console.log(array1);
// expected output: Array [4, 5, 1, 2, 3]

```

##### slice

The **`slice()`** method returns a shallow copy of a portion of an array into a new array object selected from `start` to `end` (`end` not included) where `start` and `end` represent the index of items in that array. The original array will not be modified.

```js
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

console.log(animals.slice(2));
// expected output: Array ["camel", "duck", "elephant"]

console.log(animals.slice(2, 4));
// expected output: Array ["camel", "duck"]

console.log(animals.slice(1, 5));
// expected output: Array ["bison", "camel", "duck", "elephant"]

```

##### splice

The **`splice()`** method changes the contents of an array by removing or replacing existing elements and/or adding new elements in place.

```js
const months = ['Jan', 'March', 'April', 'June'];
months.splice(1, 0, 'Feb');
// inserts at index 1
console.log(months);
// expected output: Array ["Jan", "Feb", "March", "April", "June"]

months.splice(4, 1, 'May');
// replaces 1 element at index 4
console.log(months);
// expected output: Array ["Jan", "Feb", "March", "April", "May"]

```

