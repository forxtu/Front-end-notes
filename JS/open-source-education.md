## Open source education
To not use word `new` we can create`init` function and Object.create()
```js
var Person = {
  init: function(firstName, lastName) {
    this.firstName = firstName || 'Default';
    this.lastName = lastName || 'Default';
  },
  
  getFullName: function(firstName, lastName){
    return this.firstName + ' ' + this.lastName;
  }
}

var den = Object.create(Person);
den.init('Den', 'M');

console.log(den.getFullName()); // Den M
```