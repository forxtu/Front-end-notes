# Fat arrow function =>

### Fat arrow function refers to the place where it is written and regular `function` refers to the place where it is called

In case we call function with `()` - `this` always will refers to the `window`.

## The main point of `this` in arrow functions:

**Arrow function does not have** a `this` on their own like regular **functions**. Only regular function and global scope has `this` of their own.

#### Which would mean that whenever `this` would be referred in **arrow funciton**, it will start looking **up the scope** to find the value of `this`.

In this case, during look up it found, that the object is not having a `this` of it's own, hence, it went upto global scope, and binded the value of `this` with global scope, where it wont find our `name` or anything.

```javascript
const profile = {
  name: "Alex",
  getName: () => {
    console.log(this); // looks up and doesn't see 'this' inside object so refers to the 'window'
    return console.log(this.name);
  }
};

var name = "Den"; // if we won't declare value here getName() will return undefined and error
profile.getName(); // will return 'Den' because 'this' is pointing to the window object
```

### We have to wrap **fat arrow** in function to get `this` of the needed object, because `function` has her own `this`

```javascript
const profile = {
  name: "Alex",
  getName: function() {
    console.log(this); // object
    return (() => {
      console.log(this); // object
      console.log(this.name); // Alex
    })();
  }
};

var name = "Den"; // won't be displayed because it's 'global window name'
profile.getName(); // Alex
```
