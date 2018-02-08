# Classes

## Use of classes and Inheritance
### Main points:
- constructor for properties
- To use parent's constructor we should use `super(options)` with passed arguments in constructor
- To extend parent's method we should use `super.methodName()` in the method of child

```javascript
class Car{
    constructor(options){
        this.title = options.title;
    }

    honk(){
        console.log('beep');
    }
}

class Honda extends Car{
    constructor(options){
        super(options); // extend parent's Constructor: Car.constructor
        this.color = options.color;
    }

    honk(){
        super.honk(); // extend parent's method
        console.log('beep from honda');
    }
}
var civic = new Honda({title: 'civic', color: 'black'});
civic.title; // civic - extended from Car
civic.color; // black
civic.honk(); // 'beep' and then 'beep from honda'
```