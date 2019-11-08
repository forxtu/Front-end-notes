## Hoisting

> Setup Memory space for variables and functions
> It's not actually moving code declarations to the top but register memory space - looks like moving to the top

```js
b(); // Called b
console.log(a); // undefined - we don't have error because of hoisting

var a = "Hello";

// for function declaration works fine
function b() {
  console.log("Called b");
}
/*****/
// the same as
var a;
console.log(a);
a = "Hello";

// If we will try to execute function expression
c(); // will get an error c is not a function
var c = function() {
  console.log("Called c");
};
c(); // Called c
```

## Execution Context

1. Global Execution Context - myVar = 1;
2. a() execution context - myVar = 2;
3. b() execution context - myVar = undefined;

```js
/*
 * In order:
 * 1
 * 2
 * undefined
 * 1
 */
function b() {
  var myVar;
  console.log(myVar); // undefined
}
function a() {
  var myVar = 2;
  console.log(myVar); // 2
  b();
}
var myVar = 1;
console.log(myVar); // 1
a();
console.log(myVar); // 1
```

## Coercion

Automatic conversion to another type

## Default values

```js
function greet(name) {
  name = name || "<Your name here>";
  console.log("Hello" + name);
}
greet(); // Hello <Your name here>
```

## JSON

```js
jsonVar = {
  firstName: "Denis",
  secondName: "M"
};

var jsonStr = JSON.stringify(jsonVar);
console.log(jsonStr); // json to string - "{\"firstName\":\"Denis\",\"secondName\":\"Merkulov\"}"

var jsonObj = JSON.parse(jsonStr); // string to the json object
console.log(jsonObj);
console.log(jsonObj.firstName); // Denis
```

## By value vs By reference

**By Value (primitives)**
Create a new copy of a value

```js
var a = 3;
var b;
b = a; // new spot in memory for b
a = 2;
// because they have 2 separate copies in memory
console.log(a); // 2
console.log(b); // 3
```

**By Reference (all objects (including functions))**
Copy link and point to the same object

```js
var c = { greeting: "hi" };
var d;
d = c; // pointing to the same spot in memory
c.greeting = "hello"; // mutate property
console.log(c.greeting); // hello
console.log(d.greeting); // hello
```
