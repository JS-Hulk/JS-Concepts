# JS-Concepts

## Functions
1.Function expressions vs function declarations
function sumA(a, b) {
  return a + b;
}

(function sumB(a, b) {
  return a + b;
});

sumA(1, 2); // ???
sumB(1, 2); // ???

The explanation is that sumA was created using a function declaration, which creates a function variable (with the same name as the function name) in the current scope. But sumB was created using a function expression (it is wrapped into parentheses), which doesn’t create a function variable in the current scope

If the statement starts with the function keyword, then it’s a function declaration, otherwise it’s a function expression.

// Function declaration: STARTS with `function` keyword
function sumA(a, b) {
  return a + b;
}

// Function expression: DOES NOT START with `function` keyword
const mySum = (function sumB(a, b) {
  return a + b;
});

// Function expression: DOES NOT START with `function` keyword
[1, 2, 3].reduce(function sum3(acc, number) { 
  return acc + number 
});

Function declarations are expected inside the global scope or the direct the scope of other functions:
Using the same reason it is not recommended to use function declarations inside conditionals (if) and loops (while, for):

There are 2 kinds of functions created inside a function expression:

If the function inside the expression doesn’t have a name, e.g. function() { return 42 }, then that’s an anonymous function expression
If the function has a name, e.g. sumB and callback in the previous example, then that’s a named function expression


## Array
1. reduce
array.reduce(function(accumulator, item, index, array) {
  // Use `accumulator` and `item` 
  // to calculate `updatedAccumulator`...
  return updatedAccumulator;
})
example: 
const numbers = [2, 4, 6];

const sum= numbers.reduce((sum, item)=>{
  const updatedSum= sum+item;
  return updatedSum
}, 0)
console.log(sum)

You can also omit the second argument of the array.reduce(). In such a case the reduce method initializes the accumulator value with the first item of the array, and the iteration starts from the second item.

 Immutable merge of arrays
 a. Merge using the spread operator
 const heroes = ['Batman', 'Superman'];
const villains = ['Joker', 'Bane'];
const all = [...heroes, ...villains];
all; // ['Batman', 'Superman', 'Joker', 'Bane']

b. Merge using array.concat() method
example:
const heroes = ['Batman', 'Superman'];
const villains = ['Joker', 'Bane'];

const all1 = heroes.concat(villains);
const all2 = [].concat(heroes, villains);
all1; // ['Batman', 'Superman', 'Joker', 'Bane']
all2; // ['Batman', 'Superman', 'Joker', 'Bane']

Mutable merge of arrays
a. Merge using array.push() method
const heroes = ['Batman'];
heroes.push('Superman');
heroes; // ['Batman', 'Superman']

const heroes = ['Batman', 'Superman'];
const villains = ['Joker', 'Bane'];
heroes.push(...villains);
heroes; // ['Batman', 'Superman', 'Joker', 'Bane']

## The Difference Between Values and References in JavaScript
// Primitives
const number = 10;
const bool = false;
const str = 'Hello!';
const missingObject = null;
const nothing = undefined;

// Objects
const plainObject = {
  prop: 'Value'
};
const array = [1, 5, 6];
const functionObject = (n1, n2) => {
  return n1 + n2;
};

Values:
The simple rule of passing by value is that all primitive values in JavaScript are passed by value. Simple as that.
Passing by value means that every time you assign a value to a variable, a copy of that value is created. Every single time

References:
When creating an object you’re given a reference to that object. If 2 variables hold the same reference, then changing the object reflects in both variables.

Array.sort
const numbers = [10, 5, 11];
numbers.sort(); // => [10, 11, 5]

a. array.sort() without arguments : array.sort() is a method on array instance that sorts the array in place (mutates the original array) and returns the sorted array.
const names = ['joker', 'batman', 'catwoman'];
names.sort(); // => ['batman', 'catwoman', 'joker']

b. array.sort() with a comparator:const mutatedArray = array.sort([comparator]);
If comparator(a, b) returns:

A negative number < 0: then a is placed before b
A positive number > 0: then b is placed before a
Zero 0: then the position of the compared elements doesn’t change
const numbers = [10, 5, 11];

numbers.sort((a, b) => {
  if (a < b) {
    return -1;
  }
  if (a > b) {
    return 1;
  }
  return 0;
}); // => [5, 10, 11]

If a < b — the function returns -1, placing a before b (e.g. 5 < 8, thus 5 is before 8)
If a > b — the function returns 1, placing b before a (e.g. 10 > 3, thus 3 is before 10)
If a === b — order is not changed.

c. Sorting using a typed array
const numbers = [10, 5, 11];

const sortedNumbers = [...new Float64Array(numbers).sort()];
sortedNumbers; // => [5, 10, 11]


array.at(index):
The limitation of the square brackets syntax:
const fruits = ['orange', 'apple', 'banana', 'grape'];
const item = fruits[1];
item; // => 'apple'

array.at(index):
const fruits = ['orange', 'apple', 'banana', 'grape'];
const item = fruits.at(1);
item; // => 'apple'

The real magic happens when you use a negative index with array.at() method — then the element is accessed from the end of the array.
const fruits = ['orange', 'apple', 'banana', 'grape'];
const lastItem = fruits.at(-1);
lastItem; // => 'grape






## This
const object = {
  message: 'Hello, World!',

  logMessage() {
    console.log(this.message); // What is logged?
  }
};

setTimeout(object.logMessage, 1000);
After a delay of 1 second, undefined is logged to console. Try the demo.

While setTimeout() function uses the object.logMessage as a callback, still, it inovkes object.logMessage as a regular function, rather than a method.
And during a regular function invocation this equals the global object, which is window in the case of the browser environment.

## How to invoke a method
Method invocation:
const world = {
  who: 'World',

  greet() {
    console.log(this === world);
    return `Hello, ${this.who}!`;
  }
};

// Method invocation
world.greet(); // logs true

const greetFunc = world.greet;
// Regular function invocation
greetFunc(); // => logs false

Indirect function invocation:
function greet() {
  return `Hello, ${this.who}!`;
}

const aliens = {
  who: 'Aliens'
};

greet.call(aliens); // => 'Hello, Aliens!'
greet.apply(aliens); // => 'Hello, Aliens!'
greet.call(aliens) and greet.apply(aliens) are both indirect method invocations. this value inside the greet() function equals aliens object.

Bound function invocation:
function greet() {
  return `Hello, ${this.who}!`;
}

const aliens = {
  who: 'Aliens'
};

const greetAliens = greet.bind(aliens);
greetAliens(); // => 'Hello, Aliens!'

Arrow functions as methods:
const world = {
  who: 'World',

  greet: () => {
    return `Hello, ${this.who}!`;
  }
};
world.greet(); // => 'Hello, undefined!'




## Promise
Why Promises Are Faster Than setTimeout()?
Promise.resolve(1).then(function resolve() {
  console.log('Resolved!');
});

setTimeout(function timeout() {
  console.log('Timed out!');
}, 0);

// logs 'Resolved!'
// logs 'Timed out!

The event loop:
The call stack is a LIFO (Last In, First Out) structure that stores the execution context created during the code execution. In simple words, the call stack executes the functions.

Web APIs is the place the async operations (fetch requests, promises, timers) with their callbacks are waiting to complete.

The task queue (also named macrostasks) is a FIFO (First In, First Out) structure that holds the callbacks of async operations that are ready to be executed. For example, the callback of a timed out setTimeout() — ready to be executed — is enqueued in the task queue.

The job queue (also named microtasks) is a FIFO (First In, First Out) structure that holds the callbacks of promises that are ready to be executed. For example, the resolve or reject callbacks of a fulfilled promise are enqueued in the job queue.

Finally, the event loop permanently monitors whether the call stack is empty. If the call stack is empty, the event loop looks into the job queue or task queue, and dequeues any callback ready to be executed into the call stack.

 Job queue vs task queue:
 
-------------------------------------------------------------------------------------------------------------------------------------------------------------
## Iterator, Generator and Yield
https://www.javascripttutorial.net/es6/javascript-iterator/

Generator: ES6 introduces a new kind of function that is different from a regular function: function generator or generator.
A generator can pause midway and then continues from where it paused. For example:

function* generate() {
    console.log('invoked 1st time');
    yield 1;
    console.log('invoked 2nd time');
    yield 2;
}
let result = gen.next();
console.log(result);
Code language: JavaScript (javascript)
Output:

invoked 1st time
{ value: 1, done: false }

Generators are created by the generator function function* f(){}.
Generators do not execute its body immediately when they are invoked.
Generators can pause midway and resumes their executions where they were paused. The yield statement pauses the execution of a generator and returns a value.
Generators are iterable so you can use them with the for...of loop.

let i = [ 1,2,3,4]

let iterator = i[Symbol.iterator]()

console.log(iterator.next())
console.log(iterator.next())
console.log(iterator.next())
console.log(iterator.next())
console.log(iterator.next())
// output:{
  done: false,
  value: 1
}
{
  done: false,
  value: 1
}
{
  done: false,
  value: 2
}
{
  done: false,
  value: 3
}
{
  done: false,
  value: 4
}
{
  done: true,
  value: undefined
}

.....
function *generator(){
	yield 1;
  yield 2;
  yield 3;
  yield 4;
}
let iterator = generator()
console.log(iterator.next())
console.log(iterator.next())
console.log(iterator.next())
console.log(iterator.next())
console.log(iterator.next())
....
function *infiniteGenerator(){
	let i=0;
  while(true){
  	yield i;
    i++;
  }
}
let iterator = infiniteGenerator()
console.log(iterator.next())
console.log(iterator.next())
console.log(iterator.next())
console.log(iterator.next())
console.log(iterator.next())
....
function *generator(){
 yield 1;
 yield* anotherGenerator();
 // return "hello"
 yield 3;
}

function *anotherGenerator(){
	yield 2;
}

let iterator = generator()
console.log(iterator.next())
console.log(iterator.next())
console.log(iterator.next())
console.log(iterator.next())
console.log(iterator.next())

returning any value will stop the generator
....


Yield: 
The yield keyword allows you to pause and resume a generator function (function*).
The following shows the syntax of the yield keyword:
[variable_name] = yield [expression];

https://stackoverflow.com/questions/2282140/whats-the-yield-keyword-in-javascript

 
