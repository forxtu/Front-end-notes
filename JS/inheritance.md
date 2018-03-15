# Inheritance
One object gets access to the properties and methods of another object.

## Functional inheritance
To make child access to the property it should be written in `this`. 
Underscore in variable name says that is variable is local and better don't change it.
```js
// Inheritance in functional style  - using call, apply
function Animal(speed, width, height) {
  
   var type = 'cats'; // local variable of function and not available in Cat
  
   this._sad = true;
   this.pat = function() {
       this._sad = false;
   }

   this.speed = speed;
   this.width = width;
   this.height = height;

   this.move = function() {
       return speed++;
   }
}

function Cat() {
   Animal.apply(this, arguments); // inheritance - use 'Animal' in 'this' object and take Animal's arguments here

   this.pat(); // pat the cat
   alert(this._sad); //false
}

var johny = new Cat(100, 30, 20);

console.log(johny.width); //30
console.log(johny.height); //20
console.log(johny.move()); //100
console.log(johny.move()); //101
console.log(johny.move()); //102

console.log(johny.type); // no access
```

## Prototype style of inheritance
- We need to make Child.prototype inherit from Parent.prototype
- Rabbit.prototype = Object.create(Animal.prototype);
- When you override the parent method in the child, you can access the original method by taking it directly from the prototype:
```js
Rabbit.prototype.run = function() {
  var result = Animal.prototype.run.apply(this, ...);
  // result -- result of the parent's method call
}
```
All structure of inheritance:
```js
// Parent class
// Constructor of the Parent
function Animal(name) {
  this.name = name;
  this.speed = 0;
}

// Methods are stored in the prototype
Animal.prototype.run = function() {
  alert(this.name + " run!")
}

// Child class
// Constructor of the Child
function Rabbit(name) {
  Animal.apply(this, arguments);
}

// Inherit
Rabbit.prototype = Object.create(Animal.prototype);

// Desirable to save constructor
Rabbit.prototype.constructor = Rabbit;

// Methods of the child
Rabbit.prototype.run = function() {
  // Call parent's method inside of own
  Animal.prototype.run.apply(this);
  alert( this.name + " jump!" );
};

// Ready, we can create objects
var rabbit = new Rabbit('rabbit');
rabbit.run();
```

Such inheritance is better than a functional style, since it does not duplicate methods in each object.
In addition, there is still an implicit, but very important architectural difference.
Often, a constructor call has some side effects, for example, affects the document. If the parent's constructor has some behavior that needs to be redefined in the child, it's impossible in a functional style.
In other words, in the functional style in the process of creating Rabbit, you must always call Animal.apply (this, arguments) to get the parent methods - and if this Animal.apply except adding methods says: "Moo-uh!", Then this is the problem :
```js
function Animal() {
  this.walk = function() {
    alert('walk')
  };
  alert( 'Moo-uh!' );
}

function Rabbit() {
  Animal.apply(this, arguments); // how to rid of 'Moo-uh!' but get 'walk'?
}
```
... Which is not in the prototype approach, because in the process of creating a new Rabbit, we do not have to call the parent's constructor. After all, the methods are in the prototype.
Therefore, the prototype approach should be preferred to the functional one as faster and more universal.