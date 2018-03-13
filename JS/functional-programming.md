# Function programming
```js
var arr1 = [1, 2, 3];
var arr2 = [];

for(var i = 0; i < arr1.length; i++) {
  arr2.push(arr1[i] * 2);
}

console.log(arr1); // 1, 2, 3 
console.log(arr2); // 2, 4, 6
```
We could do something like this using **functional programming**
```js
function mapForEach(arr, func) {
  var newArr = [];
  
  for(var i = 0; i < arr.length; i++) {
    newArr.push(
      func(arr[i])
    )
  }
  return newArr;
}

var arr1 = [1, 2, 3];
var arr2 = mapForEach(arr1, function(item) {
  return item * 3;
});

console.log(arr1); // 1, 2, 3
console.log(arr2); // 3, 6, 9

// Check limiter - preset default parameter using bind
var checkLimit = function(limiter, item) {
  return item > limiter;
}

var arr4 = mapForEach(arr1, checkLimit.bind(this, 2)); // check if elements in array > 2
console.log(arr4); // [false, false, true]


// Simplify to not call bind manually all the time
var checkLimitSimplified = function(limiter) {
  return function(limiter, item) {
    return item > limiter;
  }.bind(this, limiter);
}

var arr5 = mapForEach(arr1, checkLimitSimplified(1));
console.log(arr5); // [false, true, true]
```