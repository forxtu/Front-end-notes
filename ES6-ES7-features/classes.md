# Classes

## Use of classes and Inheritance

### Main points:

- constructor for properties
- To use parent's constructor we should use `super(options)` with passed arguments in constructor
- To extend parent's method we should use `super.methodName()` in the method of child

```javascript
class Car {
  constructor(options) {
    this.title = options.title;
  }

  honk() {
    console.log("beep");
  }
}

class Honda extends Car {
  constructor(options) {
    super(options); // extend parent's Constructor: Car.constructor
    this.color = options.color;
  }

  honk() {
    super.honk(); // extend parent's method
    console.log("beep from honda");
  }
}
var civic = new Honda({ title: "civic", color: "black" });
civic.title; // civic - extended from Car
civic.color; // black
civic.honk(); // 'beep' and then 'beep from honda'
```

## Static methods

Use for an utilities functions. Those methods are not going into prototype

```js
class Car {
  constructor(color, price) {
    this.color = color;
    this.price = price;
  }

  static comparePrices(car1, car2) {
    return Math.abs(car1.price - car2.price);
  }
}

let redCar = new Car("red", 100);
let blueCar = new Car("blue", 150);

console.log(Car.comparePrices(redCar, blueCar)); // 50
```

## Object assign to not use a lot of this in constructor

```js
class A {
  constructor(a, b, c, d, e) {
    Object.assign(this, { a, b, c, d, e });
  }
}

class B extends A {
  constructor(f, ...args) {
    super(...args);
    this.f = f;
  }
}

let b = new B("f in child", "a", "b", "c", "d", "e");

console.log(b); // 'f in child' , 'a', 'b', 'c', 'd', 'e'
```
