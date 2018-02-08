# Destructuring

## Destruct object
```javascript
var obj = {
    name: 'Den',
    sex: 'male'
}

// ES5
var name = obj.name;
var sex = obj.sex;

// ES6 - we are saying: Create variable 'name' and pull property from the object with the same name
const { name } = obj;
const { sex } = obj;
// we can combine them like this
const { name, sex } = obj;
```

## Also we can **destruct** arrays
```javascript
var companies = [
    'Google',
    'Facebook',
    'ABB'
];
/* create var name1 and pull companies first element from array:
   var name1 = companies[0];
   var name2 = companies[1]; etc */
const [ name1, name2, name3 ] = companies;
console.log(name1); // Google
console.log(name2); // Facebook
console.log(name3); // ABB

console.log(name4); // undefined

const { length } = companies;
console.log(length); // 3 - number of the elements
```
### To desctruction a **propery** we are using `{}` . And to destruction an **element** we are using `[]`

```javascript
var comps = [
    { name: 'Google', location: 'Mountain View'},
    { name: 'Facebook', location: 'Menlo park'}
]
// to access to the location of the Google ES5:
var location = comps[0].location; // Mountain View

// using destructuring ES6
var [ location ] = comps; // Step 1: [] gives us first entire object in 'comps'
var [{ location }] = comps; // Step 2: {} destructuring of 'location' property in first object (Google)
```

## Another example
```javascript
const Google = {
    locations: ['Mountain View', 'New York', 'LA'];
}

// We are saying - using {locations} - first look at this Google object and find 'locations' property
// and then using [ location ] pull off the first element
const { locations : [ location ] } = Google; // Mountain View
```

## Practical use of destructuring
```javascript
// ES5 syntax
function signUp(options){ // set needed arguments
    console.log(options.username + options.password + options.email + options.city);
}
var user = {
    username: 'myname',
    password: 'mypassword',
    email: 'example@example.com',
    city: 'mycity'
}
signUp(user);

// ES6 using destructuring
function signUp({username, password, email, city}){ // take those properties from object and we can put arguments in different order
    console.log(username + password + email + city); // we don't have to user 'options.' all the time
}
var user = {
    username: 'myname',
    password: 'mypassword',
    email: 'example@example.com',
    city: 'mycity'
}
signUp(user);
```