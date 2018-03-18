# Conditionals & loops
data
```js
data: {
    show: true,
    users: [
        {name: 'Bob'},
        {name: 'Alex'}
    ]
}
```
## **v-if, v-else, v-show**
```js
// if
<p v-if="show">This is shown</p> // add or remove element from dom
<p v-else>This is not</p>
<button @click="show = !show">Switch</button>

// `template` for multiple elements
<template v-if="show">
    <h1>Hey</h1>
    <p>How are you?</p>
</template>

// show
<p v-show="show">This is shown</p> // display block/none
```

## **for** loop
```js
<li v-for="(user, index) in users" :key="user">
    {{user.name}} {{index}}
</li> // Bob, Alex li elements

// multiple
<template v-for="(user, index) in users">
    <h1>{{user.name}}</h1>
    <p>{{index}}</p>
</template>

// loop through properties of object
<li v-for="user in users">
    <div v-for=(value, key) in user">
        {{key}}: {{value}}
    </div>
</li>

// Loop through numbers
// 12345678910
<span v-for="n in 10">
    {{n}}
</span> 
```