
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
