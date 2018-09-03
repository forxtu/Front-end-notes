## Prototypes

### How to set Prototype of an Object

```js
let objProto = {
  greet() {
    console.log(this.greeting + " world!");
  }
};

// 1 method **Object.create*(objProto)*  - preferable method
let obj1 = Object.create(objProto);
obj1.greeting = "Hi";
obj1.greet();

// 2 method **create function constructor**
let Greeting = function(term) {
  this.greeting = term;
};
Greeting.prototype = objProto;
let obj2 = new Greeting("Hola");

obj2.greet();

// 3 method **use Object.setPrototypeOf(obj, objProto) - ES6** - slow method
let obj3 = {
  greeting: "Hello"
};

Object.setPrototypeOf(obj3, objProto);

obj3.greet();
```
