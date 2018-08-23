## Arrays

```js
// returns the selected elements to a new array
// i - from which index we begin
// j - how many items we take
array.splice(i, j)

// returns the selected elements to a new array
// i - from which index
// j - to what index
array.slice(i, j)

// does not return a new array, changes the old one, changes the order of the elements
array.reverse();

// unifies 2 arrays, does not change old arrays, only returns a new one
arr1.concat(arr2);

// converts an array to a string, we specify how to separate the elements
var array = [1, 2, 3];
array.join(‘, ‘); // “1, 2, 3”
```

### Array-like arguments object

```js
let arg = function(firstname, lastname) {
  /* convert arguments from an Array-like object to the normal Array */

  // let args = Array.prototype.slice.call(arguments);
  // var args = (arguments.length === 1 ? [arguments[0]] : Array.apply(null, arguments));

  // ES2015
  // let args = Array.from(arguments);
  let args = [...arguments];

  args.map(item => {
    console.log(item);
  });
};

arg("Den", "M"); // Den M
```
