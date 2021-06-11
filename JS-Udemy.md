```js


// Speed Limit = 70
// increse 5 -> 1 points
// Math.floor(1.3)
// 12 points -> suspend

checkSpeed(80)

function checkSpeed(speed){
  let countVoilation = 0;
  let speedLimit = Math.floor((speed -70)/5)

  if( speed <=70){
    console.log("OK")
  }
  else if(speed > 70 && speedLimit <12){
      console.log(speedLimit)
  }
  else if(speedLimit >=12){
    console.log("DL cancelled")
  }
}
```
----------------------------------------------------------------------------------------------------------------------------

```js

// count truthy values

// Falsy
// undefined
// null
// 0
// ''
// NaN
// false

const array =  [0, undefined, null, 1, 2, 3,4]

function countTruthy(array){
  let count =0;
  for(let value of array){
    if(value){
      count++
    }
  }
  return count
}

console.log(countTruthy(array))
```

------------------------------------------------------------------------------------------------------------------------

```js

// mutliply of 3 below 10: 3,6,9
// multiply of 5 below 10: 5,10
// sum =>33

function sum(limit){
  let sum = 0;

  for(let i=1; i<=limit;i++){
    if(3*i <=10){
      sum += 3*i
    }
    if(5*i <=10){
      sum += 5*i
    }
  }
  return sum
}

console.log(sum(10))
```
--------------------------------------------------------------------------------------------------------------------------------------------

```js
// Print starts

function star(rows){
  for(let row=1; row<= rows; row++){
    let pattern = '';
    for(let i=0; i<row; i++){
      pattern += '*'
     
    }
     console.log(pattern)
  }
}

star(5)
```

-----------------------------------------------------------------------------------------------------------------------------------------------

```js
// Prime number (whose factors are 1 and itself)
// Composite
// 12 = 1,2,3,4,6,12 can be divided by its factors evenly
// 11 , 13 

showPrime(20)

function showPrime(limit){
  for(let number=2; number <=limit; number++){
    let isPrime = true;
    for(let factors=2; factors< number; factors++){
      if(number % factors === 0) {
        isPrime = false;
        break;
      }
    }
    if(isPrime) console.log(number)
  } 
}
```

-------------------------------------------------------------------------------------------------------------------------------------------------

```js

// in order to prevent the repeating of the Object we can have factory function

// Factory function

function createCircle(radius){
  return{
    radius,
    draw(){
        console.log('draw')
    }
  }
}

const circle1= createCircle(1)
console.log(circle1)
// try circle1.constructor
const circle2= createCircle(2);
console.log(circle2)


// Constructor function: job is to create/construct the object
// we should name with pascal notaion: OneTwoThree

function Circle(radius){
  this.radius = radius;
  this.draw= function(){
    console.log("draw")
  }
}
// from the above it is clear that fucntions are object
const circle3= new Circle(1)
// try circle3.constructor
console.log(circle3)


// dynamically adding property to Object

const circle= {
  radius: 1
}

circle.color ="red"

delete circle.color

console.log(circle)

```
--------------------------------------------------------------------------------------------------------------------------------------------

```js
// Fucntions are objects

function Circle(radius){
  this.radius = radius;
  this.draw = function(){
    console.log("Draw")
  }
}

// this here is refers to below {}
// Circle.call({}, 1)
// Circle.apply({}, [1,2,3])

// we can also create with Fucntions
const Circle1= new Function('radius', `
  this.radius = radius;
  this.draw = function(){
    console.log("Draw")
  }
`)

const circleFunction = new Circle1(1)
console.log(circleFunction)

const circle1= new Circle(1)
console.log(Circle.constructor)
console.log(circle1)
```
-----------------------------------------------------------------------------------------------------------------------------------------------------

```js

// Primitives are copied by the value
// Objects are copied by the reference

// Primitive
let x=10;
let y=x;

x=20
console.log(y)


let number= 10;

function increment(number){
  number++
}
increment(number)
console.log(number)



// Reference
let a={value: 20};
let b=a;
a.value=100;
console.log(b)

let number= {value: 10};

function increment(number){
  number.value++
}
increment(number)
console.log(number)

```

-----------------------------------------------------------------------------------------------------------------------------------------------

```js
// Enumerating Properties of Object
// Object is the bult in constructor function

const circle={
  radius: 1,
  draw: function(){
    console.log("draw")
  }
}

for(let val in circle) console.log(val)

for(let val of Object.keys(circle)) console.log(val)

for(let entries of Object.entries(circle)) console.log(entries)

if("radius" in circle) console.log("yes")

```
--------------------------------------------------------------------------------------------------------------------------------------------

```js
// Cloning an Object
const circle={
  radius: 1,
  draw: function(){
    console.log("draw")
  }
}

// older way of copying
let another ={};
for(let val in circle){
  another[val] = circle[val]
}
console.log(another)

// new way
let another1= Object.assign({}, circle)
console.log(another1)

// we can use spread operator
let another2= {...circle}
console.log(another2)
```

-----------------------------------------------------------------------------------------------------------------------------------------------

```js


// Garbage Collection
// like other launguage we are not allocating any memory. it is automatically created
// As a JS developer no need to worry about memory allocation. Garbage collector will automatically assign and garbage collected with some complex algorithm runnign in background

```
------------------------------------------------------------------------------------------------------------------------------
