## Closures

```js
function greet(whatToSay) {
  return function(name) {
    console.log(whatToSay + " " + name);
  };
}
greet("Hey")("Den"); // Hey Den

// Executing context is gone after function is done but the 'whatToSay' variable is still there in memory space
var sayHi = greet("Hi");
// whatToSay -> Hi
// sayHi function has no variable whatToSay and looking up for it -> because of closure it is still there
sayHi("Den"); // Hi Den
```

```js
function buildFunctions() {
  var arr = [];

  // i = 0 -> 1 -> 2 -> 3 now it's greater than 3, quit the loop
  for (var i = 0; i < 3; i++) {
    arr.push(function() {
      console.log(i); // But what if we want print 0, 1, 2? *second example
      // console.log(i++); // gives after each call of function 'i greater than previous' 3 -> 4 -> 5
    });
  }

  return arr;
}

let fs = buildFunctions();

// they all have the same parent and looking up by scope chain
fs[0](); // 3
fs[1](); // 3
fs[2](); // 3
```

\*second example -
If we want to print 0, 1, 2

```js
function buildFunctions2() {
  var arr = [];

  for (var i = 0; i < 3; i++) {
    // scope 'i' variable
    let j = i;
    arr.push(function() {
      console.log(j);
    });
    // or
    // execute function on each iteration to create different executing contexts for every 'i'
    arr.push(
      (function(j) {
        return function() {
          console.log(j);
        };
      })(i)
    );
  }

  return arr;
}

let fs2 = buildFunctions2();

fs2[0](); // 0
fs2[1](); // 1
fs2[2](); // 2
```
