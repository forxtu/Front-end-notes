# Method chaining

To make it pissible we need `return this` in function

```js
var Obj = function() {
    this.i = 0;
    
    this.add = function(i) {
        this.i += i;
        return this; // to get object instead if 'undefined'
    }
    
    this.substract = function(i) {
        this.i -= i;
        return this;
    }
    
    this.print = function() {
        console.log(this.i);
    }
}

var x = new Obj();

// x.add(3);
// x.substract(2);
// x.print();

x.add(3).substract(2).print(); // 1
```


## Private methods
```js
var Obj = function() {
    var i = 0;
    
    var add = function(j) {
        i += j;
        return this;
    }
    
    var substract = function(j) {
        i -= i;
        return this;
    }
    
    var print = function() {
        console.log(i);
    }
    // return methods like this
    return {add: add, substract: substract, print: print};
}
// we don't need a new keyword anymore
var x = Obj();

x.add(3).substract(2).print(); // 1
```