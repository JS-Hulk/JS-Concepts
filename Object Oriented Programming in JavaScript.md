
## Constructor
```js
//Function noraml

const add = function(num1, num2){
  return num1+ num2
}

let sum = add(1,2)

// Constructor function
const CarColor= function(color){
  this.color = color
}

let redCar= new CarColor('red')

console.log(redCar)
```

```js
// we can have private value because of the closure
let Car= function(_color){
    this.setColor = function(color){
        _color = color
    }
    this.getColor = function(){
        return _color
    }
}

let redCar= new Car('red')

console.log(redCar.getColor())
```
## Prototype
every constructor has the property called prototype and you can add methods to it.__proto__ is the creator of that instance
proto is the creator of the object which inside has one more proto which is the master object.
```js
const Car = function(color){
    this.color= color;
    // normally this we will have in the function
    // this.getColor=function(){
    //     return this.color
    // }
}
Car.prototype.getColor=function(){
    return this.color
}

//we can shadow the master obejct
Object.prototype.toString= function(){
    return `color: ${this.color}`
}

let redCar= new Car('red');
console.log(redCar.getColor())
console.log(redCar.toString())
```
