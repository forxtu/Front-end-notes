## Call

```js
var obj = {
   num: 3
}
var addToThis = function(a, b) {
   return this.num + a + b;
};

console.log(addToThis.call(obj, 1, 2)); // 6
```

## Apply
>The same as call but you can pass arguments as an array
```js
var arr = [2, 2];
console.log(addToThis.apply(obj, arr)); // 7
```

## Bind
>Bound new function to the object and use it in the object context
```js
var bound = addToThis.bind(obj); // bound new function to the obj
console.log(bound(3, 2)); // path arguments from 'addToThis' function like in .call
```

## Function borrowing
We have 2 different 'persons' but 2nd one doesn't have `fetFullName` function. So we can use that function in the 'person2' context
```js
var person = {
  firstName: 'Den',
  lastName: 'M',
  
  getFullName: function(arg1, arg2) {
    var fullName = this.firstName + ' ' + this.lastName;
    return fullName + ' ' + arg1 + ' ' + arg2;
  }
}

var person2 = {
  firstName: 'Hania',
  lastName: 'S'
}

console.log(person.getFullName.apply(person2, ['hey,', 'how are you?'])); // Hania S hey, how are you?
```

## Function currying
>Creating a copy of a function but with some preset parameters
```js
function multiply(a, b) {
    return a * b;
}
var multipleByTwo = multiple.bind(this, 2); // we are setting first value 'a' to 2
/* similar to this
function multipleByTwo(b) {
    var a = 2;
    return a * b;
}
*/
multipleByTwo(4); // setting second parameter 'b' to 4: '2 * 4 = 8'
```