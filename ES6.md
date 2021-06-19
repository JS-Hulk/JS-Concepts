### forEach
Iterator function is the function we passed into the forEach.
```js
const colors = ['red', 'green', 'yellow'];

//es5
for(let i=0; i< colors.length; i++){
  console.log(colors[i])
}

//es6
colors.forEach((color)=>{
  console.log(color)
})

// adding the elements of the array
let number = [1,2,3,4,5]

let sum = 0;

number.forEach((ele)=>{
  sum+=ele
})
console.log(sum)
```

----------------------------------------------------------------------------------------------------------

### Map

```js
const number = [1,2,3]
const doubleNumber = [];

// es5
for(let i=0; i< number.length; i++){
  doubleNumber.push(number[i]*2)
}
console.log(doubleNumber);

//es6
let double = number.map((number)=>{
  return number *2
})
console.log(double)

//pluking the object
let cars=[
  {model: "maruthi", price: "Cheap"},
  {model:"Audi", price: "high"}
]

cars.map((ele)=>{
  console.log(ele.price)
})
```

--------------------------------------------------------------------------------------------------------

### filter
```js
const vehical =[
  {model: "brezza", type: "car"},
  {modal: "royal enfiled", type:"bike"},
  {modal: "fiat", type: "car"},
  {modal: "honda shine", type:"bike"}
]

const filteredArray = [];

for(let i=0; i< vehical.length;i++){
  if(vehical[i].type=== 'bike'){
    filteredArray.push(vehical[i])
  }
}
console.log(filteredArray)

const filtered = vehical.filter((ele)=>{
  return ele.type === "bike"
})
console.log(filtered)
```
Create a function called ‘reject’. Reject should work in the opposite way of ‘filter’ — if a function returns ‘true’, the item should *not* be included in the new array. Hint: you can reuse filter.
```js
var numbers = [10, 20, 30]; 
//define a function 'reject' which takes array and a function
function reject(array, iteratorFunction) {
  return array.filter(function(item) {
      return !iteratorFunction(item); 
  });
}
//call the function 'reject' and assign the value to the variable 'lessThanFifteen'
var lessThanFifteen = reject(numbers, function(number) {
    return number > 15;
});
lessThanFifteen;
```
------------------------------------------------------------------------------------------------------------------

### find
```js
let names =[
  {name: "shubham"},
  {name: "vinayak"},
  {name: "Nirmala"}
]

let user;
for(let i=0; i< names.length;i++){
  if(names[i].name==="shubham"){
    user = names[i];
    break;
  }
}
console.log(user)

let name = names.find((user)=> user.name === "shubham")
console.log(name)


// Custom findWhere Helper
var ladders = [
  { id: 1, height: 20 },
  { id: 3, height: 25 }
];

function findWhere(array, criteria) {
  // ES6 style
  return array.find(item => {
    return item[Object.keys(criteria)] === criteria[Object.keys(criteria)];
  });
}

findWhere(ladders, { height: 25 })
```

-------------------------------------------------------------------------------------------------------------------------

### 
