# Objects
4 different ways to create objects
```js
// 1
var person = {
    name: 'Den'
};

// 2
var person = new Object();
person.name = 'Den';

// 3
var person = Object.create(null); // we can pass another object 'Object.create(Person)
person.name = 'Den';

// 4
function Person(){
    this.name = 'Den';
}
var person = new Person();
```

## Reflection
An object can look at itself, listing and changing its properties and methods.
```js
var person = {
    firstName: 'default',
    lastName: 'default',

    getFullName: function() {
        return this.firstName + ' ' + this.lastName;
    }
}
var den = {
    firstName: 'Den',
    lastName: 'M'
}
den.__proto__ = person; // for demo purposes only
for (var prop in den) {
    if (den.hasOwnProperty(prop)) { // won't show getFullName
        console.log(prop + ': ' + den[prop]);
    }
}
```

## Function constructors
A normal function that is used to construct objects. The `this` variable points a new empty object, and that object is returned from the function automatically
```js
function Person(firstName, lastName){
  
    this.firstName = firstName;
    this.lastName = lastName;
  
    // If we add methods like this inside function and create 1000 objects we will have 1000 methods greeting and that will slow down our app
    this.greeting = function() {
        return this.firstName + ' ' + this.lastName;
    }
}

var den = new Person('Den', 'M');
console.log(den.greeting()); // Den M

var hania = new Person('Hania', 'S');
console.log(hania.greeting()); // Hania S
```

## Prototype
It's better to put your methods in prototype to have only 1 copy to use
```js
// If we add methods in prototype we will have it only once
Person.prototype.greeting = function() {
    return this.firstName + ' ' + this.lastName;
}
```

## Object.create and Pure Prototypal Inheritance

```js
var person = {
  firstname: 'Default',
  lastname: 'Default',
  
  greet: function() {
    return this.firstname + ' ' + this.lastname;
  }
}

var person1 = Object.create(person);
person1.firstname = 'Den';
person1.lastname = 'M';
console.log(person1.greet()); // Den M
```

## ES6 and Classes

```js
class Person {
  constructor(firstname, lastname){
    this.firstname = firstname;
    this.lastname = lastname;
  }
  
  greet() {
    return this.firstname + ' ' + this.lastname;
  }
}

let den = new Person('Den', 'M');
console.log(den.greet()); // Den M
```