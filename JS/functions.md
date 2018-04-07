# Functions

## Function declaration
```js
a(); // we can involve function before it's delared, function available in memory because of hoisting
function a() {
    console.log('function a');
}
```
## Function expression
```js
b(); // error undefined is not a function
var b = function() {
    console.log('function b');
}
```
## Immediately Invoked Functions Expressions (IIFEs)
```js
var greet = function(name){
  console.log('Hey ' + name);  // Hey Den
}('Den');
// IIFE
(function(){
    console.log('Hey ');
}());

// IIFE override global var
var greeting = 'Hello';
(function(global, name){
  var greeting = 'Hey';
  global.greeting = 'Hey';
  console.log(greeting + ' ' + name); // Hey Den
}(window, 'Den'));

console.log(greeting); // Hey
```

## Factories (using **closures**)
> Every time you call a function it get it's own execution context and any function created inside this function will point to that execution context
1. Global Execution context created
- greetEnglish
- greetPolish
- makeGreeting()
2. Call `makeGreeting('en')` - created new execution context for function and removes it leaving the variable `language 'en'`
3. Call `makeGreeting('pl')` - created new execution context for function and removes it leaving the variable `language 'pl'`
4. `() 'greetEnglish'` function object points to the `language 'en'` using **closure**
5. `() 'greetPolish'` function object points to the `language 'pl'` using it's own **closure**
```js
function makeGreeting(language) {
  
  return function(firstName, lastName) {
    if(language === 'en') {
      console.log('Hello ' + firstName + ' ' + lastName);
    } else if(language === 'pl') {
      console.log('Hej ' + firstName + ' ' + lastName);
    }
  }
}

var greetEnglish = makeGreeting('en'); //
var greetPolish = makeGreeting('pl');

greetEnglish('Den', 'M'); // Hello Den M
greetPolish('Hania', 'S'); // Hej Hania S
```

## Callback function
**A function you give to another function, to be run when the other functon is finished**
So the functon you call, 'calls back' by calling the function you gave it when it finishes.
```js
function tellMeWhenDone(callback) {
  // some work here
  var a = 3;
  var b = 2;
  var c = a + b;
  console.log(c);
  // then callback
  callback();
}

tellMeWhenDone(function() {
  console.log('done');
});
// 5, 'done'
```

## Recursion
Function which returns itself
```js
let add = function(n) {
  if(n < 0){
    return 0;
  } else {
    return n + add(n - 1);
  }
}

console.log(add(3)); // 6
// mechanism
add(3) => 3 + add(2);
          3 + 2 + add(1);
          3 + 2 + 1 + add(0);
          3 + 2 + 1 + 0 = 6
```