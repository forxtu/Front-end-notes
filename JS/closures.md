## Closures

```js
function greet(whatToSay) {
    return function(name) {
        console.log(whatToSay + ' ' + name);
    }
}
greet('Hey')('Den'); // Hey Den

var sayHi = greet('Hi');
sayHi('Den'); // Hi Den
```