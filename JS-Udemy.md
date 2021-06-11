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

```js
// String

// Primitive type of String
let str = "shubham"
console.log(typeof(str)) //string 

// Reference/Object type
let str1= new String('shubham');
console.log(typeof(str1)) //Object

// template literals we have ``
```

-------------------------------------------------------------------------------------------------------------------------------------

```js
// Exercise1 

const  address ={
  street: "main road",
  city: "bangalore",
  zipCode: 560045,
}

function showAddress(address){
  // console.log(`street: ${address.street}
  // city: ${address.city}
  // zipCode: ${address.zipCode}`)

  for(let val in address){
    console.log(val, address[val])
  }
}

showAddress(address)
```

--------------------------------------------------------------------------------------------------------------------------------------------------

```js
// Exercise2

const  address ={
  street: "main road",
  city: "bangalore",
  zipCode: 560045,
}

// Factory function
function addressFactory(street, city, zipCode){
  return {
      street,
      city,
      zipCode
  }
}

let address1= addressFactory("main road", "bangalore", 581455)
console.log(address1)

// Constructor function
function addressConstructor(street, city, zipCode){
  this.street = street
  this.city = city
  this.zipCode = zipCode
}
let address2= new addressConstructor("main road", "Bangalore", 564500)
console.log(address2)
```
---------------------------------------------------------------------------------------------------------------------

```js
// Exercise3

// Constructor function
function addressConstructor(street, city, zipCode){
  this.street = street
  this.city = city
  this.zipCode = zipCode
}
let address1= new addressConstructor("main road", "Bangalore", 564500)
let address2= new addressConstructor("main road", "Bangalore", 564500)


function areEqual(address1, address2){
  return address1.street === address2.street && 
  address1.city === address2.city &&
  address1.zipCode === address2.zipCode
}

function areSame(address1, address2){
  return address1 === address2
}

console.log(areEqual(address1, address2)) //true
console.log(areSame(address1, address2)) //false
```

--------------------------------------------------------------------------------------------------------------------------------------------

```js
// Array

const number = [3, 4];

// start
number.unshift(1,2)
console.log(number)

// end
number.push(5,6)
console.log(number)

// middle
number.splice(2, 0, 'a', 'b')
console.log(number)

// Finding elements primitive type
const a= [1,2,3,4,5,1,7,3,4]
console.log(a.indexOf(1)) //0
console.log(a.indexOf('a')) // -1
console.log(a.lastIndexOf(1)) //5
console.log(a.includes(4)) // true

// Finding the elemet refernce type
const courses = [
  {id: 1, name:'a'},
  {id: 2, name: 'b'}
]
console.log(courses.includes({id:1, name:'a'})) // false

// we can use findIndex also
const course = courses.find(function(course){
  return course.name === 'a'
})
console.log(course) // {id: 1, name:'a'}

// Removing elements from Array

const number = [1,2,3,4,5,6]

//end
const last= number.pop()
console.log(last)
console.log(number)

//start
const start= number.shift()
console.log(start)
console.log(number)

// middle
const middle = number.splice(3, 2)
console.log(middle)
console.log(number)

// emptying Array
let number1 = [1,2,3,4,5,6]

//solution 1
number1 = [];

//solution 2
number1.length = 0;

// solution 3
number1.slice(0, number1.length)

// solutiopn 4
while(number1.length > 0){
  number1.pop()
}

// Combining and slicing array

let first = [1,2,3];
let second = [4,5,6];

//let combined = first.concat(second)
let combined = [...first, ...second]
console.log(combined)

let sliced = combined.slice(2)
console.log(sliced)

// Iterating an array
const numbers= [1,2,3,4,5,6]

for(let number of numbers) console.log(number)

numbers.forEach((number, index) => console.log(number, index))

//Joining array
const number1= [1,2,3]
const number2 = number1.join(',')
console.log(number2) //

let str= "this is the example string "
let str1 =  str.split(' ')
console.log(str1)
console.log(str1.join('-'))

// Sorting Array
const number = [3,2,1]
console.log(number.sort())
console.log(number.reverse())

const courses = [
  {id:1, name: "Node"},
  {id:2, name: "Js"}
]
courses.sort((a,b)=>{
  // a>b =>1
  // a<b =>-1
  // a===b =>0
  if(a.name >b.name) return 1;
  if(a.name < b.name) return -1
  return 0;
})
console.log(courses)

// Testing the elements of the array
const number1= [1, 2, 3, -5,10]

const a= number1.every((value)=>{
  return value>=0
})
console.log(a)

const b= number1.some((value)=>{
  return value>=0
})
console.log(b)

// Filter the array
const c= number1.filter(number => number>=0)
console.log(c)

// Map in Array
const d= c.map(n => ({value: n}))
console.log(d)

// Reducing array
const reducedArray = number1.reduce((accu, current)=> accu+current,2)
console.log(reducedArray)
```

------------------------------------------------------------------------------------------------------------------------------------------------

