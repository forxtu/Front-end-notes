# Array Helpers

## forEach
We are pass items in to the Iterator function one by one
```javascript
let array = [1, 2, 3];

array.forEach(function(item){
    console.log(item); // 1, 2 ,3
});
```
We can declare function out of forEach method and then pass it
```javascript
function log(item){
    console.log(item);
}

array.forEach(log);
```

## map
We are not making changes in the original array, we are creating new one and pass returned parameters
```javascript
let array = [1, 2, 3];

let doubled = array.map(function(item){
    return item * 2; // 'return' required
});
console.log(doubled);  // [2, 4, 6]
```

## filter
filter returns new array
```javascript
let array = [1, 2, 3, 4, 5];

let filtredArray = array.filter(function(item){
    return item > 3; // 'return' required
});
console.log(filtredArray);  // [4, 5]
```

## find
Find and return only first coincidence
```javascript
let users = [
  {name: 'Jim'},
  {name: 'Alex'},
  {name: 'Den', id: 4},
  {name: 'Den'}
]

let findUser = users.find(function(user){
  return user.name === 'Den';
});

console.log(findUser); // will return object with id: 4
```

## every & some
Returns boolean value
&& - and
|| - or
```javascript
let computers = [
  {ram: 4},
  {ram: 12},
  {ram: 16}
]

let computerEvery = computers.every(function(computer){
  return computer.ram > 8;
});
console.log(computerEvery); //false, because 1 computer has 4

let computerSome = computers.some(function(computer){
  return computer.ram > 8;
});
console.log(computerSome); //true, because atleast 1 computer has more than 8
```

## reduce
#### Reduces array to one element. 
On first iteration it takes init value 0 and add first element '10'. On second iteration we have 10 value + 20. And then 30 + 30. Summ is 60
```javascript
let numbers = [10, 20, 30];

let summ = numbers.reduce(function(sum, number){
  return sum + number;
}, 0); // 0 here is an initial value

console.log(summ); // 60
```

Another example how do we take 'previous' value and add to the next
```javascript
let primaryColors = [
  {color: 'red'},
  {color: 'yellow'},
  {color: 'green'}
];

let colors = primaryColors.reduce(function(previous, primaryColor){
  previous.push(primaryColor.color); // push color to the array
  
  return previous;
}, []); // empty array as init value

console.log(colors); // ['red', 'yellow', 'green']
```